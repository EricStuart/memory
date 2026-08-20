# Non-code follow-up notes

Record count: 1

# Task Group: %USERPROFILE%\Documents\Codex\2026-06-30\ton plain-language medical and local-history follow-up answers
scope: Direct-answer, non-code follow-ups in this thread after the token audit, especially early-pregnancy hCG interpretation and village-level Li-surname origin questions where the user wants practical next steps or explicit evidence boundaries.
applies_to: cwd=%USERPROFILE%\Documents\Codex\2026-06-30\ton; reuse_rule=Reuse for similar plain-language Q&A patterns and routing cues, but re-browse current medical or historical sources when accuracy is time-sensitive and avoid treating this block as repo-specific code guidance.

## Task 1: Interpret the hCG pattern `470 -> 480` in 2 days, then `480 -> 2000` in 2 days, success

### rollout_summary_files


### keywords

- hCG, early pregnancy, 470 -> 480, 480 -> 2000, 48 hours, progesterone, transvaginal ultrasound, ectopic, heavy bleeding, shoulder pain

## Task 2: Explain likely Li-surname family-origin lines near Dingzhou and Quyang, success

### rollout_summary_files


### keywords

- 瀹氬窞, 鏇查槼, 鏉庡, genealogy, 瀹惰氨, 瀛楄緢, 鍫傚彿, ancestral tomb, 璧甸儭鏉庢皬, 涓北鏉庢皬

## User preferences

- when the user follows a medical interpretation with questions like `鍚庣画濡備綍鍙戝睍`, `鍚庣画妫€鏌ヤ粈涔堥」鐩甡, or `浠€涔堟椂鍊欏彲浠ユ瘮杈冪ǔ瀹歚, move quickly to the monitoring plan, timing, and danger signs instead of staying at abstract interpretation [Task 1]
- when the user asks a local surname-history question like `娌冲寳瀹氬窞鏇查槼闄勮繎鐨勬潕濮撳鏃忓巻鍙叉潵婧恅, stay local and evidence-bounded instead of drifting into broad surname lore [Task 2]
- when the request is a plain-language follow-up rather than code work, keep the answer concise and actionable instead of overloading it with technical process detail [Task 1][Task 2]

## Reusable knowledge

- The discussed hCG pattern was a concerningly slow rise from `470` to `480` over 48 hours followed by a much better rise from `480` to `2000` over the next 48 hours; the durable answer pattern was to say early hCG does not have to `double` exactly, then shift to follow-up confirmation rather than certainty claims [Task 1]
- The practical follow-up guidance that fit this question was: repeat hCG at 48 hours if needed, treat progesterone as an auxiliary marker rather than a stand-alone decision tool, and arrange transvaginal ultrasound once hCG is around `2000`, with `3500-4000+` as a stronger threshold for ultrasound expectations [Task 1]
- The stability milestones given were intrauterine gestational sac, then fetal heartbeat, then lower risk after `8-10` weeks, and generally more stability after `12` weeks; urgent-care red flags were unilateral pain, shoulder pain, dizziness/syncope, or heavy bleeding [Task 1]
- For the Dingzhou/Quyang Li-surname question, the safe durable answer was that the region has multiple plausible lines, including local associations with `璧甸儭鏉庢皬` / `涓北鏉庢皬` plus common Ming-era migration narratives, and that region alone is not enough to prove one branch [Task 2]
- The strongest genealogy-routing clues to request next are the village name, `瀛楄緢`, `鍫傚彿`, family-tree pages, or tomb inscriptions; those carry more discriminative value than the county name by itself [Task 2]

## Failures and how to do differently

- Symptom: a medical answer sounds decisive without enough dating or ultrasound context. Cause: the numbers are being treated as diagnosis instead of trend interpretation. Fix: keep the answer probabilistic, give the monitoring plan and urgent red flags first, and ask for exact timing details only if they are required to avoid ambiguity [Task 1]
- Symptom: a local surname-history answer overstates one lineage from the region name alone. Cause: broad county-level history is being mistaken for a family-specific genealogy. Fix: say explicitly that `瀹氬窞銆佹洸闃抽檮杩?+ 鏉庡` is insufficient for one-origin certainty and ask for village-level genealogy clues if the user wants a stronger identification [Task 2]
- Symptom: a plain-language question triggers unnecessary technical detail or artifact creation. Cause: the session context started with a code/data task. Fix: notice the task-family shift and answer directly in chat when no local file or repo action is actually needed [Task 1][Task 2]
