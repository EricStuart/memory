# Codex 使用量分析经验

英文完整记录：[../codex-usage.md](../codex-usage.md)

- 可用数据源包括 sessions、archived_sessions、session_index 和 `logs_2.sqlite`；详细 token 总量以 rollout JSONL 中的 `token_count` 事件为准。
- 跨事件统计应累加 `last_token_usage.total_tokens`，不能累加会重复计算的 `total_token_usage`。
- 模型维度需要从最近的 `session_meta` 或 `turn_context` 回填；无法匹配的事件保留为 `unknown`。
- 统计结果是带截止时间的快照；分析过程仍会写入新事件，因此重复计算可能出现轻微漂移。
- 场景分类不能只依赖 cwd，还要结合线程标题中的项目、引擎或功能关键词。

