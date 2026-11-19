# Research, writing, and design

这是一个可以跨项目使用的 Codex Skill，覆盖完整科研流程，也能直接处理局部写作、设计评审和方案简化。当前仓库采用 Codex 的项目级技能路径。

## 快速开始

在 Codex 桌面端打开 `D:\MyProject\research-writing-design` 文件夹。使用 Codex CLI 时，也可以在 PowerShell 里启动。

```powershell
Set-Location -LiteralPath 'D:\MyProject\research-writing-design'
codex
```

在 Codex 聊天里发送下面这条请求。示例自带实验数据，可以直接试用。

```text
$research-writing-design 只写一句英文 Results。Dataset A 使用同一数据划分、训练预算和种子，基线 B1 的 macro-F1 为 71.5%，改动 W1 为 73.0%。把结果写直接，结论限定在这次比较。
```

预期得到一句英文结果，保留 Dataset A、比较条件和两组分数。如果写提升量，单位是 1.5 个百分点。

## 常用场景

在请求开头加上 `$research-writing-design`，说明当前阶段、相关材料和想要的交付物。下面的文件名可以替换成你项目里的路径，材料也可以直接贴进聊天。

| 场景 | 示例请求 | 预期得到 |
| --- | --- | --- |
| 科研全流程 | 从 `idea.md` 出发，推进文献定位、基线与对照设计、实验分析和英文论文结果。复用已有产物，先列下一项能验证核心假设的实验。 | 研究缺口、实验计划、已有证据支持的结论和待完成事项。 |
| 实验设计或结果分析 | 对照 `configs/` 和 `runs/results.csv`，检查基线与改动的评估条件是否可比，汇总已有结果，并给出一项最有区分力的消融。 | 可比较的指标和差异、证据位置，以及待验证的判断。 |
| 论文写作或审稿回复 | 根据 `runs/results.csv` 改写 `paper/results.tex` 的前两段。用英文写得直接，核对每个数字。或者根据审稿意见写逐条回复，说明哪些补实验已经完成。 | 指定范围的英文改写或回复，每条关键主张都能回查证据。 |
| 简化技术设计 | 评审 `design.md` 的实验记录方案。优先复用现有记录入口，指出可以删掉的包装层、重复校验、哈希检查和确认步骤，并说明应保留的边界校验。 | 可执行的删减方案、保留的行为和验收方式。 |
| 投稿前检查 | 按目标会议的年份和 track 查当届官方要求，核查 `paper/main.tex` 的匿名、页数和附录，并用项目现有命令编译。 | 已核验事项、证据位置，以及因缺少规则或编译结果仍待确认的项目。 |

局部任务可以直接限制范围，例如「只改摘要」「只检查引用」或「先评审方案，给出修改建议」。当一项材料缺失时，Skill 会标明受影响的结论，并继续完成其余部分。

## 在其他项目使用

把 [完整技能目录](.agents/skills/research-writing-design/) 复制进目标项目的 `.agents/skills/`，确保入口位于目标项目的 `.agents/skills/research-writing-design/SKILL.md`，参考文件随目录一并复制。然后从目标项目打开 Codex，继续用 `$research-writing-design` 调用。本仓库是维护源，之后按需同步整个技能目录。

如果 Codex 里找不到该 Skill，先核对当前项目目录和 `SKILL.md` 的路径。路径正确时，重新打开项目或重启 Codex。[Codex Skills 文档](https://learn.chatgpt.com/docs/build-skills)

## 维护

1. 在 [验收案例](evals/cases.md) 记下能复现的问题、最小输入和可观察的通过条件。案例使用合成或脱敏材料。
2. 只改影响该行为的入口描述或参考文档。改动涉及自动触发时，同时重跑应触发和应跳过的近邻请求。改动涉及输出时，检查主张、数据和行为，允许措辞变化。
3. 用新上下文重跑受影响案例和相邻案例，再提交。稳定版本可用 Git 标签标记。当届投稿要求在使用时查官方来源。
4. 引入上游内容时先查具体文件及其许可，记录来源、采用的做法和实际引入的版本。当前规则为独立编写。仓库内的研究资产优先使用合成或获准共享的材料。

## 上游参考

星数为 2026-11-19 查看 GitHub 时显示的约数，用作发现项目的线索。

| 上游 | 采纳的做法 | 此处的处理 |
| --- | --- | --- |
| [Anthropic Skills · 197k ★](https://github.com/anthropics/skills) | [Skill Creator](https://github.com/anthropics/skills/blob/main/skills/skill-creator/SKILL.md) 用真实请求检验触发和产出，并加入容易误触发的近邻案例。 | 保留小型案例集，手工检查可观察的结果。 |
| [Ponytail · 194k ★](https://github.com/DietrichGebert/ponytail) | 复用现有入口，最小完整改动，保留真实风险下的校验。 | 将工程判断写成针对当前行为和真实失败的简短规则。 |
| [Karpathy Autoresearch · 100k ★](https://github.com/karpathy/autoresearch) | [实验规程](https://github.com/karpathy/autoresearch/blob/master/program.md) 用固定评估条件、预算和结果记录比较迭代。 | 采用可比较的评估条件和有界迭代，沿用项目自己的训练栈。 |
| [K-Dense Scientific Agent Skills · 57.7k ★](https://github.com/K-Dense-AI/scientific-agent-skills) | [Scientific Writing](https://github.com/K-Dense-AI/scientific-agent-skills/blob/main/skills/scientific-writing/SKILL.md) 把主张和证据关联起来。 | 用原文定位、原始输出和运行 ID 追溯主张，按任务大小选择记录形式。 |
| [Orchestra AI Research SKILLs · 14.7k ★](https://github.com/Orchestra-Research/AI-Research-SKILLs) | [ML Paper Writing](https://github.com/Orchestra-Research/AI-Research-SKILLs/blob/main/20-ml-paper-writing/ml-paper-writing/SKILL.md) 检查引文以及 LaTeX 模板的原始编译。 | 投稿时查当届官方材料，论文写作和投稿检查可分别调用。 |
| [Research Paper Writing Skills · 8.4k ★](https://github.com/Master-cai/Research-Paper-Writing-Skills) | 按论文各章节提供分开的写作参考。 | 把章节指导压缩为可直接用于修改稿件的问题。 |
| [Hoemr 的 ML Paper Writing](https://github.com/Hoemr/ml-paper-writing) | 专项参考。将防御性写作视为对论证和信息结构的影响，审查主张、布局与措辞。 | 删除预先辩护和重复限定，保留可改变结论解释的限制。 |
