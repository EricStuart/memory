# Kele-1.7 隔离开发栈经验

英文完整记录：[../kele-1.7.md](../kele-1.7.md)

- 从 `release/public_1.7` 单分支克隆到独立目录，先确认分支、提交和远程分歧。
- 本地启动使用忽略的 `.runtime` 配置，不修改生产服务器配置，也不提交本地环境文件。
- 完整验证包括 Web、Gateway、NATS、PostgREST、PostgreSQL 和 Projector，而不是只访问 Web 页面。
- `legal_document_versions` 为空会导致当前法律文档接口返回 503；本地可幂等写入 terms/privacy 测试版本。
- 本地手机号/SMS 流程应关闭生产微信变量，避免 OAuth callback 指向线上域名。
- 自动迁移遇到历史 CRLF 校验问题时，使用本地忽略配置绕过，不改写迁移文件本身。

