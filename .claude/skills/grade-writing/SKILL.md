---
name: grade-writing
description: >
  Grade a writing submission holistically: correct errors with explanations, comment on
  naturalness and register, and provide a fully corrected version. Use when the learner
  submits a writing task. This is the highest-value feedback in the system. Trigger on
  "grade my writing", "review my text", "I finished the writing task".
disable-model-invocation: true
---

# /grade-writing — grade writing (holistic)

Grade the learner's writing submission. Write feedback in the **content language** defined in `CLAUDE.md`; keep the corrected text itself in the **target language**.

## Read
- `lessons/session-NNN/class/03-writing/submission-NN.md` (the learner's text) and the matching `task-NN.md`. The writing slot holds **one or more** tasks; grade each `submission-NN.md` against its `task-NN.md` (for a single task it is `-01`).

## Process
1. Correct each error inline, with a short explanation of the rule behind it (the *why*, not just the fix).
2. Comment on higher-level qualities: naturalness, register, structure, word choice — not only grammar.
3. Provide a **fully corrected version** of the text in the target language.
4. Note 2–3 recurring issues worth carrying into the weak spots (so `/close-day` can record them).

## Writes
- `lessons/session-NNN/class/03-writing/review-NN.md` (one per task, matching each `submission-NN.md`; for a single task it is `-01`).
- Append one row to `progress/scores.csv` for this writing segment (create the file with the header `session,segment,skill,items,correct,pct,self_difficulty_1to5,tier` if it does not yet exist). Use: the session number N; `segment=03-writing`; `skill=writing`; a holistic `pct` you assign (0–100) standing in for the score, with matching `items`/`correct` (e.g. `items=1,correct=1` weighted by the same pct, or leave `items=1` and let `pct` carry the signal); the learner's `self_difficulty_1to5`; and the `tier`. `/close-day` and `/recalibrate` read this curve.

Keep it rich and specific — this is where the learner gets the most signal. Avoid reducing it to a checklist.
