# Personal AI Workspace

一个 AI-native 的个人工作与学习工作台。

这里用于捕获、执行、记录和归档每一次学习与任务，并从真实工作中逐步沉淀长期知识、可复用方法和 AI Skills。

## 核心循环

```text
捕获 → 执行 → 归档 → 沉淀
```

1. 把尚未整理的想法、资料或任务放入 `inbox/`。
2. 使用 `templates/work-item/` 在 `work/active/` 创建一个工作单元。
3. 在同一目录内记录目标、过程、来源、决策和最终产物。
4. 完成后总结结果，判断是否产生长期知识或 Skill 候选。
5. 将工作单元移入 `work/archive/<year>/`。

## 导航

- [WORKSPACE.md](WORKSPACE.md)：定位、边界和运行机制。
- [AGENTS.md](AGENTS.md)：AI 在本项目中的工作规则。
- `work/`：每一次具体工作及其完整上下文。
- `knowledge/`：从多次工作中提炼出的长期有效知识。
- `.agents/skills/`：经过验证、正式生效的项目级 Skills。
- `skill-lab/`：候选 Skills 的孵化、评估和退役记录。
- `templates/`：工作单元和其他可复用模板。
- `system/`：工作台自身的维护与演进记录。

## 工作单元命名

使用 `YYYY-NNN-short-name`，例如：

```text
work/active/2026-001-learn-rag/
```

简单任务只需保留必要文件；复杂任务再增加来源、决策和更多产物。记录应服务于理解和复用，避免为了完整而制造负担。

## 信息分层

- 只与一次工作有关：保留在对应的 `work/` 目录。
- 多次工作后仍然有效：提炼到 `knowledge/`。
- 可重复执行但尚未稳定：放入 `skill-lab/candidates/`。
- 已验证且具备清晰触发条件：发布到 `.agents/skills/`。
