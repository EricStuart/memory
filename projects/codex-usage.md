# Codex usage analysis notes

Record count: 1

# Task Group: %USERPROFILE%\Documents\Codex\2026-06-30\ton Codex usage analysis and local log mining
scope: Local Codex usage/accounting questions that need totals or breakdowns from `.codex` artifacts, especially when the user wants two-month token totals, model splits, or scenario splits instead of a high-level explanation.
applies_to: cwd=%USERPROFILE%\Documents\Codex\2026-06-30\ton; reuse_rule=Safe to reuse for local Codex log-mining and usage-analysis tasks on this machine, but re-read the current `.codex` artifacts and state the snapshot time because totals drift while sessions continue writing logs.

## Task 1: Summarize two months of Codex token usage totals, success

### rollout_summary_files


### keywords

- token_count, last_token_usage, total_token_usage, logs_2.sqlite, sessions, archived_sessions, session_index.jsonl, total_tokens, Beijing time, drift

## Task 2: Break down the two-month totals by model, success

### rollout_summary_files


### keywords

- gpt-5.5, gpt-5.4, unknown, turn_context.payload.model, session_meta, token_count, model backfill, monthly totals

## Task 3: Split Codex usage by work scenario (`UE 鎻掍欢寮€鍙慲 vs `kele`), success

### rollout_summary_files


### keywords

- UE 鎻掍欢寮€鍙? kele, other, cwd classification, session_index.jsonl, thread title, D:\hyli\kele, %USERPROFILE%\Documents\Unreal Projects\ue_dms_plugin, MetaHuman, LevelSequence

## User preferences

- when the user asks for "缁熻杩戜袱涓湀鐨?token 娑堣€楁€婚噺", start from local readable Codex artifacts and compute the answer directly instead of opening with abstract accounting explanations [Task 1]
- when the user follows with "鎸夋ā鍨嬪垎鍒粺璁?, keep drill-down-capable fields available and continue the breakdown instead of stopping at the grand total [Task 2]
- when the user reframes the question as "UE 鎻掍欢寮€鍙戝拰 kele 鍚勫崰澶氬皯", prefer classification by real work scenario rather than only by technical dimensions such as month or model [Task 3]
- for similar local log-analysis requests in this thread family, Chinese is a safe default because the user kept the analytics conversation in Chinese [Task 1]

## Reusable knowledge

- The durable local data sources for Codex usage mining on this machine are `%USERPROFILE%\.codex\sessions`, `%USERPROFILE%\.codex\archived_sessions`, `%USERPROFILE%\.codex\session_index.jsonl`, and `%USERPROFILE%\.codex\logs_2.sqlite`; `logs_2.sqlite` alone does not carry the usable token totals, so the real totals come from rollout JSONL `token_count` events [Task 1]
- For cross-event aggregation, use `token_count.info.last_token_usage`; `total_token_usage` is cumulative session state and will overcount if summed across events [Task 1]
- A complete two-month total was obtained by summing `last_token_usage.total_tokens` across all `token_count` events inside the target date window, then deriving monthly and later breakdowns from the same event stream [Task 1]
- Per-model breakdown required backfilling model labels from the nearest prior `session_meta` / `turn_context` entries because many `token_count` events do not carry model fields directly; the resulting dominant model was `gpt-5.5`, followed by `gpt-5.4`, with early unmatched events left as `unknown` [Task 2]
- `turn_context.payload.model` was the key field for later model attribution, with `session_meta.payload.model` and `collaboration_mode.settings.model` as supporting fallbacks when needed [Task 2]
- Scenario classification worked best by combining `cwd` with `session_index.jsonl` thread-title signals; `kele` matched `D:\hyli\kele*` worktrees, while `UE 鎻掍欢寮€鍙慲 matched Unreal project paths plus titles containing `UE`, `Unreal`, `DmsGen`, `MetaHuman`, `LevelSequence`, and related terms [Task 3]
- The scenario split for this environment was effectively two dominant buckets plus `other`, and the classifier needed both project paths and thread-title keywords to keep UE work from leaking into `other` [Task 3]

## Failures and how to do differently

- Symptom: SQLite schema inspection only shows migration noise and no usable accounting fields. Cause: `logs_2.sqlite` is not the authoritative source for detailed token totals. Fix: pivot quickly to rollout JSONL `token_count` events in `.codex\\sessions` / `.codex\\archived_sessions` [Task 1]
- Symptom: recomputing totals later yields slightly larger numbers. Cause: the current analysis session keeps writing new `token_count` events while the audit is running. Fix: state that the numbers are a snapshot, or freeze the session / record a cutoff timestamp before strict reconciliation [Task 1][Task 2][Task 3]
- Symptom: direct per-model grouping leaves many events unclassified. Cause: most `token_count` events do not include model fields. Fix: backfill from the most recent preceding `turn_context` / `session_meta` entry and leave genuinely unmatched early events as `unknown` instead of forcing them into a model bucket [Task 2]
- Symptom: an early scenario split undercounts `UE 鎻掍欢寮€鍙慲 and overstates `other`. Cause: some early UE threads used a generic `%USERPROFILE%` cwd. Fix: augment cwd classification with thread-title keywords such as `UE`, `Unreal`, `DmsGen`, `MetaHuman`, and `LevelSequence` [Task 3]
