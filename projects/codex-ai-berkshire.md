# AI Berkshire skill installation notes

Record count: 1

# Task Group: %USERPROFILE%\Documents\Codex\2026-08-06\an ai-berkshire Codex skill installation on Windows
scope: Install and validate the `xbtlin/ai-berkshire` Codex skills/prompts distribution, including generated-artifact drift reporting.
applies_to: cwd=%USERPROFILE%\Documents\Codex\2026-08-06\an; reuse_rule=Reuse for this repository's Windows installer workflow after checking current repository scripts, existing skill-name conflicts, and generated-output status.

## Task 1: Install ai-berkshire Codex skills and prompts, success

### rollout_summary_files

- rollout_summaries/2026-08-06T03-40-38-mEeS-install_ai_berkshire_codex_skills_windows.md (cwd=%USERPROFILE%\Documents\Codex\2026-08-06\an, rollout_path=%USERPROFILE%\.codex\sessions\2026\08\06\rollout-2026-08-06T11-40-38-019fd528-a648-78b2-8367-ad2b8631a70a.jsonl, updated_at=2026-08-06T03:47:38+00:00, thread_id=019fd528-a648-78b2-8367-ad2b8631a70a, installed 21 skills and 20 prompts; upstream prompt generation drift remained)

### keywords

- ai-berkshire, github.com/xbtlin/ai-berkshire, install-codex-skills.bat, install-codex-prompts.bat, sync-codex-skills.py --check, sync-codex-prompts.py --check, %USERPROFILE%\.codex\skills, %USERPROFILE%\.codex\prompts, codex-prompts/deep-company-series.md, 3-8 篇长文拆一家公司

## User preferences

- when the user gives a repository URL and direct installation request, execute it end to end, including conflict checks and validation [Task 1]

## Reusable knowledge

- Canonical sources are `skills/*.md`; `codex-skills/*/SKILL.md` and `codex-prompts/*.md` are generated artifacts. On Windows, validate reachability, read `AGENTS.md` and installer scripts, check same-named skill conflicts, then run `cmd /c scripts\\install-codex-skills.bat` and `cmd /c scripts\\install-codex-prompts.bat`. [Task 1]
- Validate generation with `py -3 scripts\\sync-codex-skills.py --check` and `py -3 scripts\\sync-codex-prompts.py --check`; a Codex restart is required before newly installed skills/prompts become available. [Task 1]

## Failures and how to do differently

- Symptom: a conflict-check PowerShell pipeline fails with an empty pipeline element. Cause: malformed empty pipeline input. Fix: correct the pipeline and re-run the conflict check before installing. [Task 1]
- Symptom: generation checks expose `codex-prompts/deep-company-series.md` text mismatch (`看懂XX公司（深度公司系列）：3-8 篇长文拆一家公司` versus committed `深度公司系列：8 篇长文拆一家公司`). Cause: upstream generated artifact drift. Fix: report the remaining `M codex-prompts/deep-company-series.md` accurately and decide separately whether to keep generated output or update/commit the canonical source. [Task 1]
