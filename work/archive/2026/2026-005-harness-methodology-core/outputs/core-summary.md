# 核心方法论总结

## 一句话

这是一套把大需求从高方差的自然语言问题，逐级编译为可由 AI 零上游决策执行的契约闭包任务，并用可验证状态机控制执行、失效和学习回流的方法论及其可执行实现。

## 核心推导

1. 大需求包含大量决策点、隐式约束和跨模块语义依赖，整体正确性会随 N 增长而快速下降；`P^N` 是结构性风险启发式，不是严格概率公式。
2. 收敛来源分为 N1 与 N2：N1 是模块内部本可通过工程准备消除的返工；N2 是问题域固有的跨模块语义耦合，只能枚举、锁定和验证。
3. 不能直接从需求拆 checklist。必须先发现决策面，再锁定产品与工程决策；决策面来自经验型 trigger 和针对当前需求的生成型压力测试。
4. 模块不是按目录或调用方向划分，而由 authoritative writer、owned state/data/resource、状态机闭合和独立变化能力确定。
5. 跨模块耦合不能消失，因此要建立 Module Contract Graph，把 Trigger、Normal、Failure、Consistency、Timing、Verification 显式化。
6. PRD、AIP、考古、迁移、前端契约、验证矩阵等 artifact 是强类型中间表示，不是最终交付物；它们的责任是保持语义可追踪、可审查、可验证并可向下游投影。
7. 将全局语义按 canonical owner 降解为最小 executable obligations，再按同一模块、语义类型、operation/surface 和短验证闭环生成 contract-closed Atomic Issues。
8. Atomic Issue 是 sealed execution packet：包含前提、consumed contract snapshot、provided obligation、invariant、禁止重决策、精确文件与步骤、验证预期和失败回流；执行者不应回读全局文档补猜。
9. 验证是设计输入；局部验证之外还必须证明 provider/consumer 组合、真实生产副作用、前端 action flow、runtime materialization 和 acceptance boundary。
10. Workflow 用 receipt、hash、DAG、admission、allowlist 和 backflow invalidation 管理可信状态；上游语义变化会使派生任务和证据失效并触发重算。
11. 复盘把收敛项归类为 N1/N2；重复 N1 必须前移为 trigger、artifact obligation、validator 或 regression rule，使方法本身持续学习。

## SDD 的位置

`proposal/spec/plan/tasks` 只是容器和导航结构。方法论的质量模型来自决策面闭合、模块与契约、语义消费、验证、Atomic Issue 和状态门禁，而不是 SDD 模板本身。
