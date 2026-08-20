# Kele-1.7 isolated stack notes

Record count: 1

# Task Group: D:\hyli\kele-1.7 isolated local release/public_1.7 development stack
scope: Windows clone provisioning, complete local runtime startup, personal-registration legal-document seeding, and strict server-impact isolation.
applies_to: cwd=D:\hyli\kele-1.7; reuse_rule=Reuse only for this checkout's ignored .runtime launchers, ports, and local database context.

## Task 1: Clone release/public_1.7 and verify the complete isolated local stack, success

### rollout_summary_files

- rollout_summaries/2026-08-18T09-27-42-euXa-clone_release_1_7_and_isolate_local_dev_stack.md (cwd=\\?\D:\hyli\kele-1.7, rollout_path=\\?\%USERPROFILE%\.codex\sessions\2026\08\18\rollout-2026-08-18T17-27-42-01a01432-b469-77d1-b931-94de0116326c.jsonl, updated_at=2026-08-18T10:57:53+00:00, thread_id=01a01432-b469-77d1-b931-94de0116326c)

### keywords

- git clone, release/public_1.7, .runtime/restart-local-stack.ps1, AUTO_MIGRATE_ON_DEV, 127.0.0.1:3000, 8088, 8222, 55433, Projector, legal_document_versions, local-dev-2026-08-18, no server impact

## User preferences

- when the user says 拉取, finish clone/pull and verify branch and divergence; when the user says 不要影响服务器, keep workarounds in ignored .runtime/.env.runtime, restore tracked files, create no deployment commit, and verify a clean branch.

## Reusable knowledge

- Empty target: git clone --branch release/public_1.7 --single-branch ... .; stale GCM state may require credential cleanup and git -c credential.interactive=never. Final clone was f3bd1d28 with 0/0 divergence.
- Local stack uses ignored launchers and verifies Web 3000, Gateway 8088, NATS 8222, PostgREST 55433, and Projector. Empty legal_document_versions causes /api/legal/documents/current 503; idempotently seed terms/privacy as local-dev-2026-08-18 and disable local WeChat variables for phone/SMS onboarding.

## Failures and how to do differently

- Interactive clone can stall after browser authorization; abort the partial checkout and retry noninteractively. Historical CRLF checksum failure in 20260529_add_manual_shot_video_prompt.sql is handled with ignored AUTO_MIGRATE_ON_DEV=false, not a tracked workaround. Raw Windows ESM loader paths fail; use file:///D:/... . Local OAuth must not target the production callback domain.
