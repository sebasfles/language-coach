---
name: recalibrate
description: >
  Periodically re-estimate the learner's level and adjust the plan's pace. Run every 28th session,
  aligned with the 90-minute test. Reads the per-skill scores curve, weak-spots churn, the period's
  session recaps, and the latest 90-minute test result, re-estimates CEFR level per skill, updates
  STATE.md, adjusts the roadmap pace if the learner is ahead of or behind plan, and appends a
  level-history row. Trigger on "recalibrate", "re-check my level", "adjust the plan".
disable-model-invocation: true
---

# /recalibrate — re-estimate level, adjust pace

Run this **every 28th session**, aligned with the 90-minute test. Re-estimate the learner's level against **real data, not the average**. Write in the **content language** defined in `CLAUDE.md`.

## Read first (explicit — don't plan from memory)
As your FIRST action, Read each of these files (`cat ... 2>/dev/null` is fine); treat any missing file as empty; do not plan from memory:
- `progress/scores.csv` — the trailing curve for the **objectively-graded** skills (reading, writing-holistic, grammar, `00-check`). Weight the 90-minute test heaviest, with the every-7th-session 15-minute tests as corroboration; read the per-skill trend, not a single row.
- `weak-spots.md` — which spots are still `active`/`watch` vs `cleared`, and how much each churned.
- The period's session recaps (`lessons/session-*/recap.md`) — drill into the relevant ones if you need detail; the **listening** and **speaking** self-report notes here are your evidence for those two self-reported skills (they are not in `scores.csv`).
- The latest **90-minute test** — the `05-test/review.md` from the most recent session whose number is a multiple of 28.

**Missing-input guard.** If no 90-minute test exists yet, estimate from the recaps and the scores curve instead, and say so plainly in your summary.

## Process
1. Re-estimate the CEFR level **per skill** (reading, listening, writing, speaking) from the evidence — expect it to be asymmetric. Reading, writing, and grammar come from `scores.csv` plus the 90-minute `05-test` review. **Listening and speaking are self-reported skills**: estimate both from the recap self-report notes, not from `scores.csv` (neither has a graded segment to score).
2. Update the per-skill level estimate in `STATE.md`.
3. Compare progress to `roadmap.md`. If the learner is ahead, pull the plan forward / raise the target; if behind, ease the pace. Edit `roadmap.md` accordingly and note **what changed and why**. While here, scan the period's recaps for any **advanced grammar structure that RECURRED in the input** (reading/listening) across sessions — the input signals which pulls are worth it. If one keeps showing up, you MAY flag it as a candidate to pull **forward** in `roadmap.md`. Keep this light and optional.
4. **Append one row to `progress/level-history.md`** — session `N`, the CEFR estimate per skill, and the one-line what-changed-and-why. Append only; never rewrite earlier rows.
5. Summarize the new estimate and the adjustment for the learner, honestly.

## Writes
- `STATE.md`, `roadmap.md`, and an appended row in `progress/level-history.md`.
