# 价值判断

## 总结

- 问题真实：复杂、大跨度、含隐式语义的编码任务仍存在要求歧义、上下文不可见、跨模块局部正确但组合失败、验证不足和长期漂移。
- 方向成立：把意图、决策、模块边界、契约、验证和反馈机制做成 Agent 可读且可执行的环境，与领先实践一致。
- 未被完全解决：Agent 产品、SDD 工具和研究分别覆盖执行循环、spec、task orchestration、repository legibility 和 context refinement，但没有通用系统能从欠规格意图保证复杂需求正确交付。
- 会被内建一部分：规划、搜索、测试、review、恢复、DAG、上下文选择和任务循环会越来越由 Agent 平台提供；组织特定的产品语义、风险政策、acceptance oracle 和权威决策不会凭模型升级自动产生。
- 当前项目不是已验证理论：`P^N`、N1/N2 和 contract-closed issue 是有解释力的模型，但普遍性、成本收益和因果效果缺少对照实验。

## 主要成立点

1. 需求欠规格和上下文缺失会降低 Agent 成功率，结构化预探索和问题重写可改善结果。
2. Agent 可靠性由模型与环境/接口共同决定，harness 不是模型能力的重复实现。
3. repository-local knowledge、mechanical invariants、feedback loops 和 acceptance criteria 是 Agent-first 工程的持续基础设施。
4. 上游语义变化导致派生产物失效，是实际的软件配置与证据管理问题。

## 主要薄弱点

1. `P^N` 只能作为启发式，不能当定量规律；决策非独立，且测试/反馈允许纠错。
2. “零决策执行”应限于上游规范性决策；局部实现判断无法也不应全部消除。
3. 全量前置闭合容易制造瀑布式完整性幻觉；未知机制常需原型和运行时反馈发现。
4. 所有大需求固定采用重型 artifact/gate 会产生较高成本、上下文压力和 artifact 自身漂移。
5. 单一 canonical owner 和单层任务并非适用于所有分布式/纵向切片场景。
6. receipt、rubric 和 validator 证明的是流程符合性，不等于产品正确性；需要外部 outcome oracle。
7. 当前证据以单项目经验和事后归类为主，缺少 raw Codex、主流 SDD 与本方法的对照和消融。

## 建议定位

不要定位为“保证 AI 确定性完成所有大需求的普遍理论”，而定位为：

> 面向高耦合、长周期、brownfield 大改动的风险自适应语义控制平面与可执行参考 Harness。

核心内核保留决策闭合、模块契约、验证映射、owner-specific task packet 和 backflow；领域矩阵作为按风险触发的插件；receipt/runtime 作为可替换实现。
