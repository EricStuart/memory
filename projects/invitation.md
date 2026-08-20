# Invitation mobile page notes

Record count: 1

# Task Group: D:\hyli\Invitation mobile invitation visual iteration
scope: Build or refine the mobile-first single-page invitation in `D:\hyli\Invitation`, preserving the envelope/seal interaction while applying targeted visual or bamboo-detail changes.
applies_to: cwd=D:\hyli\Invitation; reuse_rule=Reuse for this Vite/Three.js invitation checkout and its bamboo SVG/CSS implementation; re-check the current viewport, source layout, and interaction before applying design changes elsewhere.

## Task 1: Build and iteratively restyle a mobile envelope invitation, success

### rollout_summary_files

- rollout_summaries/2026-06-22T02-59-38-ZGdA-mobile_invitation_bamboo_style_iterations.md (cwd=D:\hyli\Invitation, rollout_path=%USERPROFILE%\.codex\archived_sessions\rollout-2026-06-22T10-59-38-019eed44-f068-7262-9425-88c7c4666cea.jsonl, updated_at=2026-06-22T10:05:41+00:00, thread_id=019eed44-f068-7262-9425-88c7c4666cea, mobile browser-checked Vite invitation with line-led bamboo refinements)

### keywords

- D:\hyli\Invitation, Vite, Three.js, mobile-first, envelope, seal click, bamboo SVG, bambooJointGap, getBambooSectionPath, --stem-rotate, bambooLeafCount, Vitest

## User preferences

- when refining a visual design, the user repeatedly narrowed the direction from a dark premium look to `淡雅清新，低调内敛`, then `删除阴影效果，将整体风格处理为明快优雅，以线条为主` -> preserve the core interaction and make compact, isolated visual edits rather than a broad redesign [Task 1]
- when requesting bamboo adjustments such as straight horizontal joints, inward-curving connectors, non-vertical stems, and top leaves -> treat each as a targeted SVG/CSS micro-iteration and validate it in the current mobile page [Task 1]

## Reusable knowledge

- This is a small Vite app with Three.js for the envelope scene and Vitest for pure modules; preserve tap-the-seal-to-open-the-letter behavior across restyles, then run `npm test`, `npm run build`, and a phone-sized browser check [Task 1]
- Bamboo is most controllable as separate SVG sections in `src/bambooMarkup.js`: straight `H` top/bottom edges, inward-curving `C` side edges from `getBambooSectionPath(...)`, thin `bambooJointGap = 0.45`, and top leaf clusters. Small per-stem `--stem-rotate` values in `src/styles.css` avoid a rigid vertical appearance [Task 1]
- `test/bambooMarkup.test.js` protects joints, gaps, section counts, and leaves. The final mobile DOM check showed four stems, 12 leaves, 16 sections, and no horizontal overflow [Task 1]

## Failures and how to do differently

- Symptom: bamboo feels rigid or its joints look wrong. Cause: a single polygon/clip-path cannot precisely express the requested section geometry. Fix: switch to independent SVG section paths with explicit horizontal and Bezier edges [Task 1]
- Symptom: screenshot capture stalls or tabs become stale during iterative browser checks. Cause: the in-app browser can time out after repeated interactions. Fix: reuse the existing local page/tab and fall back to DOM checks for structure, counts, and overflow [Task 1]
