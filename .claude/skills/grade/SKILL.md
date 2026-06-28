---
name: grade
description: >
  Grade a test or an objective exercise set (grammar and reading). Pass the file to grade
  as the argument. Works for any test size and for standalone exercises — size doesn't change
  how it grades. Checks each answer, gives the correct form and the reason for every error,
  and surfaces patterns worth drilling. Trigger on "grade this", "check my answers", "score my test".
argument-hint: "[path to the learner's answers file]"
---

# /grade — grade objective work

Grade the file given as `$ARGUMENTS` — the learner's **filled answer worksheet** (e.g. `answers-NN.md`, `answers.md`, or a test's `answers.md`) that `/lesson` generated with the items reproduced and blank slots the learner has filled in; its sibling task/exercise/test file in the same segment dir is the prompt to mark against. Write feedback in the **content language** defined in `CLAUDE.md`.

Items follow the **assessment item-format policy in `CLAUDE.md`** — broadly production / fill-in items plus a deliberate minority of selection items (MC / true-false / matching). Grade each by its kind (see below).

If no argument is given, grade the most-recent ungraded answers under the current session (an `answers*.md` with no matching `review*.md` beside it); if more than one is ambiguous, ask which to grade.

## Process
1. Read the prompt file and the learner's filled worksheet `answers-NN.md` (or `answers.md` for a single set) under the relevant `lessons/session-NNN/class/<segment>/` — across the objectively-graded segments, e.g. `class/00-check/answers.md` (the graded retrieval warm-up probe), `class/02-grammar/<topic>/answers-01.md`, `class/03-reading/answers-NN.md` (one or more reading exercises), or `class/05-test/answers.md` on a test session. Listening (`04-listening`) is **self-reported, not graded here**, and holistic **writing** goes to `/grade-writing`.
2. Mark each item correct/incorrect.
   - **Open / fill-in / produced answers** (cloze, transformation, short open answer, translation, context-prompted production): **accept any equivalent correct answer** — synonyms, valid alternative phrasings, and acceptable spelling/case/spacing variants all count. There is no rigid answer key; do **not** mark a right answer wrong merely because it doesn't match one expected string. Still flag genuine errors (wrong form, broken rule, unidiomatic usage) and explain the why.
   - **MC / true-false / matching** items grade **exactly** against the keyed option.
3. For every error, give the correct answer and **explain the why** — the rule behind it, not just the fix.
4. Summarize the recurring error patterns worth drilling, and record them in the review file so `/close-day` can read them and fold them into the weak-spots register.
5. Report a simple score/summary.
6. Append one row to `progress/scores.csv` (create the file with its header if missing) using the score just computed: `session, segment, skill, items, correct, pct, self_difficulty_1to5, tier`. `session` is **derived from the graded answers file's own `session-NNN/` directory path** (the file being marked), **not** from `STATE.md`'s N — so the row is correct regardless of whether `/close-day` has already advanced N; `segment` is the segment dir (e.g. `00-check`, `02-grammar`, `03-reading`, `05-test`); `skill` is the underlying skill (reading/grammar/etc.); `self_difficulty_1to5` comes from the learner's self-report if present, else leave blank; `tier` reflects the segment's current difficulty level. `/lesson` reads the trailing rows per skill to drive adaptive difficulty.

## Writes
- The graded result next to the matching answers file — the marked answers, the corrections with the *why*, and the recurring error-pattern summary — as `review-NN.md` beside `answers-NN.md` (`review-01.md` beside `answers-01.md`), or `review.md` beside a single `answers.md`. `/close-day` reads this to fold the patterns into the weak-spots register.
- One appended row in `progress/scores.csv` (see Process step 6) so `/lesson` and `/recalibrate` can track the per-skill curve.

## Scope
Size-agnostic: the short per-session check, the every-7th-session consolidation test, and the every-28th-session 90-minute (1h30) test all use this skill. Holistic **writing** is handled by `/grade-writing`, not here.
