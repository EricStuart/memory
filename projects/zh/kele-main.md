# Kele-main 分支经验

英文完整记录：[../kele-main.md](../kele-main.md)

- `analyze-script-structure` 的真实执行路径应从内部 API、Provider Gateway、Worker 执行器一路追到结构化脚本落库。
- 排查 step 生成字段消失时，分别检查 API-step 原始输出、`postProcessSegments`、保存 payload 和最终 `structured_script`，不要只看最终页面。
- 内部 API 验证依赖可信内部请求头和项目权限；未认证的直接 HTTP 探测不能替代真实登录上下文。
- 已知错误如 `BILLABLE_ACTOR_NOT_FOUND`、字段被覆盖或 `transitionNotes` 丢失，都应记录原始错误和具体边界。

