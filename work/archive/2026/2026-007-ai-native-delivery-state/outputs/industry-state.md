# 行业成熟度结论

## 判断

没有可信公开证据表明通用的软件公司已实现从欠规格原始需求到生产上线的一次性、无人类验收、无需后续收敛交付。

## 当前上限

- OpenAI：无人手写代码、Agent-to-Agent review、部分 PR 无需人工 review，可端到端修复和合并；人类仍负责优先级、用户反馈转验收标准和结果验证，产品仍发布、出错、修复。
- Anthropic Claude Code：Agent 独立执行代码循环，但官方明确由开发者定义目标、review 结果，发版决定保留在人类。
- Cognition Devin：自动测试、review、autofix 和 CI 收敛，但官方 SDLC 文档仍要求人类 review 后决定 merge。
- Factory：声称从 ticket/spec/prompt 构建 production-ready feature，并自动化 review；公开的自改进流程仍有一次 human approval，且强调 human-AI collaboration 和监督界面。

## 核心区分

1. 无人手写代码不等于无人定义需求和验收。
2. 无人工 PR review 不等于无需产品验收。
3. Agent 自动多轮修复不等于一次性完成。
4. CI 全绿不等于需求语义或上线标准完整。

## 对方法论的含义

合理目标不是消灭所有收敛，而是把收敛前移、自动化、限制传播并保留证据，使人工只处理规范性决策、验收 oracle 和不可自动取得的生产事实。
