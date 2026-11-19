---
name: research-writing-design
description: >-
  Plan and carry out research, analyze machine-learning experiments, write or
  review papers, prepare rebuttals and submissions, or simplify technical designs.
  Use for 科研全流程、文献与实验、论文论证与引用、审稿回复、设计评审，
  and requests to remove defensive prose, speculative safeguards, overengineering,
  new hash checks, or needless approval steps.
---

# Research, writing, and design

按用户要的交付物推进。只读当前需要的参考，直接使用已有材料。用户要求贯穿多个研究阶段时，沿用已有成果并衔接缺失的阶段。

| 当前任务 | 参考 |
| --- | --- |
| 研究问题、文献定位、实验设计、运行、分析与复现 | [research.md](references/research.md) |
| 论文论证、段落改写、引用、模拟审稿与 rebuttal | [writing.md](references/writing.md) |
| 技术方案、代码设计评审、简化实现或校验流程 | [engineering.md](references/engineering.md) |
| 投稿准备、会议规则、匿名、编译与补充材料 | [submission.md](references/submission.md) |

单纯拼写修复、格式转换、按给定命令执行和常规小改动，按常规直接完成。

## 共用原则

- **结论写到证据允许的位置。** 先说结果或判断，给出比较对象、评估条件和必要限制。删掉预先辩护、重复限定和空泛过渡。保留会改变读者判断的不确定性、反例和适用范围。
- **用最小完整改动满足当前需求。** 优先复用已有入口和工具。按实际输入契约和失败模式设计，在信任边界校验，保留防止现实错误和数据丢失的处理。遇到内部契约异常时，让错误可见。
- **用已有记录追溯证据。** 优先引用文件与行、表或段落、运行 ID、代码版本标签、配置和原始输出。避免加文件指纹、哈希脚本或内容校验流程。已有签名或完整性协议交给原工具执行。
- **把暂停限制在相关操作。** 清楚、可逆的工作直接推进。证据缺失时，标出受影响的结论并完成有依据的部分。权限缺失时，只暂停依赖该权限的操作。按具体风险和实际依赖决定是否需要确认。

交付前检查请求的结果。报告实际核验的内容、尚有影响的缺口和对应证据。写作、代码和研究结果按用户要求的语言和格式交付。
