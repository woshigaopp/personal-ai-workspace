# 研究判断

## 核心重构

- 模块：语义责任与变化隔离单元，由 authoritative state/resource ownership、invariants 和 change reasons 确定，不由模型上下文大小决定。
- 契约：边界上的 assume/guarantee 关系及其可观察 proof，可分层、可组合，也可表达全局不变量。
- 原子任务：在给定 Agent、Harness、验证 oracle 和风险等级下，仍保持 decision-closed、contract-closed、verification-closed、failure-contained 的最大安全执行单元。

## 通用性

元模型可跨项目复用；固定单模块、单层、固定 issue 大小、固定矩阵和固定阶段不可跨所有项目成立。探索性研发、全局性能/安全性质、跨模块迁移、创意 UI 和强耦合事务需要不同分解策略。

## 研究价值

模块化和 assume/guarantee contracts 不是新概念。潜在新贡献在于：Agent-relative atomicity、语义图到执行分区的编译、能力变化下的动态 split/merge、backflow invalidation，以及对成功率/重试成本/人工成本的实证模型。

## 可检验假设

1. 基于决策/契约/验证闭包的任务划分优于基于文件数或 token 的划分。
2. 最优任务粒度随 Agent 能力提高而扩大，但受验证可判定性和系统语义边界限制。
3. runtime adaptive decomposition 优于固定静态 DAG。
4. authoritative ownership + assume/guarantee contract 能减少组合失败和下游返工。
5. backflow invalidation 能降低旧任务/旧证据继续执行造成的缺陷。
