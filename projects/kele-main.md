# Kele-main branch notes

Record count: 1

# Task Group: D:\hyli\kele\kele-main\kele script-analysis internal API verification and 10-step contract alignment
scope: Debug `analyze-script-structure` in `D:\hyli\kele\kele-main\kele` when the user wants the real internal execution path, preserved step-generated output, or a synced 10-step backend and copy contract.
applies_to: cwd=D:\hyli\kele\kele-main\kele; reuse_rule=Reuse for this checkout's `analyze-script-structure` route family, compat workflow route, and trace/tests surfaces; re-check auth gates, step labels, and saved `structured_script` fields if the checkout changes.

## Task 1: Debug the internal script-analysis API path and preserve step-generated fields in final saved output, partial

### rollout_summary_files


### keywords

- x-workflow-internal, BILLABLE_ACTOR_NOT_FOUND, workflow_task_api_steps, postProcessSegments, transitionNotes, accent insertion, trusted internal headers, SSE progress 1..10, pnpm ts-check

## Reusable knowledge

- The local Windows fallback for this checkout is `pnpm exec next dev --turbopack --port <port>` because `pnpm dev` routes through `bash ./scripts/dev.sh` [Task 1]
- The internal route path requires trusted workflow headers and a real billable actor; otherwise the same endpoint can fail with `401` or `BILLABLE_ACTOR_NOT_FOUND` even when the route logic itself is fine [Task 1]
- `workflow_task_api_steps` is the durable place to confirm per-step trace rows, provider/model metadata, and whether the route really executed all 10 outward steps [Task 1]
- `postProcessSegments()` can erase step-generated metadata unless those fields are explicitly carried through; this was the reason step-3 qualifier formatting and step-9 `transitionNotes` disappeared from the saved `structured_script` [Task 1]

## Failures and how to do differently

- Symptom: the route returns `401` or `BILLABLE_ACTOR_NOT_FOUND` during isolated verification. Cause: the internal proxy/auth gate or actor ownership was missing from the fixture. Fix: supply trusted internal headers and attach the run/project to a real acting user before debugging deeper logic [Task 1]
- Symptom: step-generated fields appear in intermediate results but disappear from final saved output. Cause: final normalization rebuilds the segments without carrying those fields through. Fix: patch `postProcessSegments()` and verify the saved `structured_script`, not only the step traces [Task 1]
