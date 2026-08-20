# Codex environment notes

Record count: 1

# Task Group: %USERPROFILE% local Codex environment maintenance
scope: Direct Codex environment/tooling requests on this Windows machine, especially CLI upgrades, home-config provider/persistence edits, and model-switch requests where the user expects immediate action or an honest capability boundary.
applies_to: cwd=%USERPROFILE% plus local Codex tooling workflow on this machine; reuse_rule=Reuse for Codex CLI npm maintenance, Codex home `config.toml` edits, and chat-environment boundary questions on this Windows setup, but re-check installed versions, live config values, and product/UI controls when the environment changes.

## Task 1: Update the global Codex CLI to npm latest on Windows PowerShell, partial

### rollout_summary_files


### keywords

- %USERPROFILE%, Codex CLI, @openai/codex, npm install -g @openai/codex@latest, npm view @openai/codex version, codex --version, windows sandbox: spawn setup refresh, EPERM, codex.ps1, global package

## Task 2: Explain the model-switch boundary for `gpt-5.6 sol`, success

### rollout_summary_files


### keywords

- gpt 5.6 sol, gpt-5.6 sol, switch model, latest model, UI model selector, cannot change runtime model, chat environment

## User preferences

- when the user gives a terse Codex-environment request like `更新 codex 最新版` or `换成最新的模型 gpt 5.6 sol`, treat it as an immediate action request or capability-boundary check, not a discussion [Task 1][Task 2]
- when the requested environment change cannot be performed from inside chat, answer with the actual control surface instead of implying success [Task 2]

## Reusable knowledge

- On this machine, `codex` resolves to `%USERPROFILE%\AppData\Roaming\npm\codex.ps1` and the CLI is installed through the global npm package `@openai/codex`; the proven upgrade command was `npm install -g @openai/codex@latest` [Task 1]
- After a global Codex update, same-session `shell_command` calls may fail with `windows sandbox: spawn setup refresh`; treat that as a session-refresh boundary and verify from a fresh shell or restarted Codex session [Task 1]
- If npm cleanup warns with `EPERM ... codex.exe` right after the update, the likely cause is the running Codex process still locking the binary; do not force-delete first, retry verification after restart [Task 1]
- Model switching cannot be done from inside the conversation; the correct handoff is the UI/model selector [Task 2]

## Failures and how to do differently

- Symptom: the npm upgrade succeeds but every follow-up shell call fails with `windows sandbox: spawn setup refresh`. Cause: the global Codex update refreshed the running executable mid-session. Fix: stop same-session verification and rerun `codex --version` only after reopening the shell or restarting Codex [Task 1]
- Symptom: npm cleanup emits `EPERM: operation not permitted, unlink ... codex.exe`. Cause: the binary is still in use by the current Codex process. Fix: treat it as a locked-file warning, not a separate install failure, and verify from a fresh session [Task 1]
- Symptom: a model-switch request tempts a fake confirmation. Cause: the runtime model is not controllable from chat. Fix: say explicitly that the user must change it in the UI/model selector [Task 2]
