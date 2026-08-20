# Codex 本地环境维护经验

英文完整记录：[../codex-environment.md](../codex-environment.md)

- Codex CLI 通过全局 npm 包维护；升级前先确认当前解析路径、版本和 npm 全局安装位置。
- 修改 Codex home 配置时只做最小范围变更，并保留原配置备份或可恢复路径。
- Windows 下遇到 `EPERM`、脚本 shim 或 sandbox 初始化问题时，先区分 CLI 包问题、权限问题和运行时刷新问题。
- 关于 Codex 产品能力、模型、设置和自动化的说明应以当前官方文档和本地实际配置为准，不能把历史记忆当成当前状态。

