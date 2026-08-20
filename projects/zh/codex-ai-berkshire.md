# AI Berkshire 技能安装经验

英文完整记录：[../codex-ai-berkshire.md](../codex-ai-berkshire.md)

- 安装前先检查仓库可达性、`AGENTS.md`、安装脚本和本机同名技能冲突。
- canonical 来源是 `skills/*.md`；`codex-skills/*/SKILL.md` 与 `codex-prompts/*.md` 属于生成文件。
- Windows 安装使用仓库提供的 `.bat` 脚本，安装后运行两个 `--check` 同步校验。
- 生成文件出现漂移时，报告具体文件和差异，不要把生成产物漂移误报为安装失败。
- 新技能通常需要重启 Codex 才能在当前会话中生效。

