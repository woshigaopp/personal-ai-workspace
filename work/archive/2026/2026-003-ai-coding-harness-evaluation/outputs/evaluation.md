# AI Coding Harness Engineering 客观评估

## 最终判断

该项目有真实且较高的方法论价值，但当前价值主要成立于“复杂、跨模块、高风险、AutoMQ/云基础设施类大改动”。它不是一个普通大 Skill，而是：

```text
方法论
+ 21 个阶段/辅助 Skills
+ 结构化 artifact schemas
+ workflow 状态机
+ compiler / validators
+ receipt/hash/backflow runtime
```

更准确的类别是 **domain-specific AI software-delivery governance runtime**。

目前可以证明它“设计严肃、内部闭环较完整”，不能仅凭公开仓库证明它“显著降低总成本或缺陷率”。因此最准确的评价是：**高潜在价值、强工程化、有限外部证据、通用化未完成。**

## 最有价值的贡献

1. **决策面发现先于决策锁定**：指出最大风险不是决定错，而是 AI 根本没有意识到存在一个需要决定的 surface。
2. **模块契约图到契约闭包 Atomic Issue**：把任务拆分从 checklist 提升为 provider/consumer obligation、invariant 和 verification 的闭包。
3. **语义消费与反向失效**：不只做 traceability，还要求上游语义逐阶段复制/转换，并在变更时使下游 receipt 失效。
4. **验证前置和 environment ground truth**：将 command、expected result、proves、failure meaning 写入执行单元。
5. **把复盘缺陷提升为规则与 smoke test**：具备从真实失败反哺运行时的演进机制。
6. **文档与机器约束双轨**：Markdown 供人理解，YAML、compiler 和 validators 形成政策即代码。

这些单项并非全新发明，分别可对应 requirements engineering、contract-driven design、V-model、ADR、traceability、workflow engine 和 policy-as-code。项目的独特性主要在于把它们针对 coding agent 的失败模式整合成可执行系统。

## 主要问题

### 1. 证据不足

`P^N` 被正确标为启发模型，但没有公开测量 P、N 或独立性。N1/N2 来自单个 Connect 多租案例的 29 个收敛 commit 分类，缺少跨需求、跨模型、跨仓库的对照组。

当前没有公开数据证明：

- 总 wall-clock time 是否下降；
- token 和人工审核成本是否下降；
- 修复 commit、escaped defect 是否下降；
- 复杂 artifact 是否只是把实现成本搬到了前置阶段；
- validators 的 false positive / false negative 比例。

### 2. 复杂度和 Goodhart 风险

当前快照约 51,384 行、120 个文件、73 个模板、21 个 Skills、34 条 stage-construction machine rules。8 个 `SKILL.md` 超过 skill-creator 建议的 500 行上限，最大为 1,689 行，存在明显上下文和维护成本。

运行时代码包含大量正则和文本启发式检查。它能拦截结构缺失，也可能诱导 Agent 为通过 gate 填充关键词或表格，而没有真正理解语义。仓库已经意识到 compiler signal hygiene 问题，但尚无公开 precision/recall 数据。

### 3. “零决策”需要重新表述

完全零决策不可实现，也可能把局部实现选择过度前置。更稳妥的目标是：

> 实现阶段零“未授权、跨模块或影响用户语义”的新决策；允许局部、可逆、契约内的实现判断。

否则方法论容易退化成重型瀑布流程，降低探索和反馈速度。

### 4. 领域耦合较强

大量 surface 和验收模型围绕 AutoMQ、云资源、K8s、Terraform、runtime materialization、Connect playground 等。它们对该领域很有价值，但不能自动证明适用于移动端、数据科学、普通 CRUD、嵌入式或算法项目。

### 5. 分发成熟度仍有缺口

- README 标注 runtime `2026.07.14.4`，manifest 实际为 `2026.07.20.1`。
- Python/PyYAML 依赖没有独立 manifest 或安装检查。
- 仓库校验在设置正确 `CODEX_HOME` 并安装 PyYAML 后通过；直接从 clone 使用 `--skills-root` 会因部分全局路径未随 `set_root` 更新而失败。
- 只有 3 个 Skill 包含推荐的 `agents/openai.yaml`。

## 分维度评分

| 维度 | 判断 |
|---|---|
| 问题真实性 | 高：大改动中的隐式决策、跨模块语义漂移和晚验证确实存在 |
| 方法论洞察 | 高：decision-surface discovery、semantic consumption、backflow invalidation 很有价值 |
| 工程实现 | 中高：状态机、receipts、compiler、validators 和 smoke tests 已形成实物 |
| AutoMQ 内部适配 | 高潜力：明显源于真实复杂领域和收敛事故 |
| 通用 Skill 适配 | 中低：领域词汇、规模和流程重量过高 |
| 公开证据强度 | 低：缺少可复现对照实验和跨项目案例 |
| 可维护性 | 中低：规则、模板和单体 Python runtime 规模很大 |

## 建议的价值验证

不要再首先增加规则；先建立公开 evaluation harness。

选取 6–10 个真实大改动，做三组对照：

1. 普通 Coding Agent；
2. 轻量 SDD + tests；
3. 当前完整 Contextpack Harness。

至少测量：

- 首次可运行实现时间；
- 总 wall-clock、token、人工交互时间；
- 实现前 open decisions 数量；
- backflow 数量和最早发现阶段；
- review findings、修复 commits、escaped defects；
- artifact 总量及维护时间；
- validator false positive / false negative；
- 需求完成后 7/30 天缺陷数。

再做消融：去掉 decision-surface discovery、receipt/backflow、Atomic Issue compiler，观察哪个组件真正产生收益。

只有完成这一步，项目才能从“有说服力的方法论实现”升级为“有证据支持的通用 Harness Engineering 方法”。

## 最值得保留的最小核心

如果要形成对外的通用版本，建议压缩为五个不变量：

1. 发现并锁定影响产品/跨模块语义的决策面；
2. 建立 provider/consumer 契约与验证责任；
3. 编译成自包含、短验证的 Atomic Issues；
4. 用 receipt 和依赖图实现语义变更后的下游失效；
5. 用真实执行证据和复盘推动规则演进。

AutoMQ、K8s、frontend、mock acceptance 等放到领域 profile，而不是通用核心。
