# Harness Methodology Core

## 摘要

重新通读 `woshigaopp/ai-coding-harness-engineering` 的方法论主文、完整 artifact 规范、决策面发现、经验约束、阶段构造协议和 context-pack workflow 规则，纠正此前把它主要理解为 SDD 或交付治理层的偏差。

## 结论

项目的中心不是文档流程，而是一套面向大需求的“语义编译与执行控制”方法：发现决策面，锁定决策，建立模块契约图，将全局语义无损降解为 owner-specific、contract-closed Atomic Issues，并通过验证前置、receipt、DAG 和 backflow 控制执行与失效传播。

## 产物

- [核心方法论总结](outputs/core-summary.md)
