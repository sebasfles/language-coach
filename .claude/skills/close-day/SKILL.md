---
name: close-day
description: >
  Close out a study session: read this session's /grade and /grade-writing results, then write
  the session recap and regenerate the rolling root recap.md (last 5 sessions), maintain
  weak-spots.md with item-level churn, record grammar transition sessions, advance the theme
  track when the current theme is solid, regenerate LEARNING-PACE.md on cadence, refresh
  STATE.md, advance the session counter, celebrate what cleared, and commit. Use at the end of
  each session. Writes several files and commits, so it
  only runs when explicitly invoked. Trigger on "close the day", "wrap up the session", "I'm done".
disable-model-invocation: true
---

# /close-day — close the session

Close the current session. Write learner-facing content in the **content language** defined in `CLAUDE.md`.

## Read first (explicit — don't plan from memory)
As your **FIRST action**, Read each of these files (`cat … 2>/dev/null` is fine); treat any missing file as empty; do not plan from memory. Ground the recap and the weak-spots update in what was actually graded this session, not a gut feeling:
- The **objective grading** from `/grade` — every review file under `lessons/session-NNN/class/`: `00-check/review.md` (the graded retrieval warm-up that opens the session), the grammar reviews beside each `answers-NN.md` (`02-grammar/<topic>/review-NN.md`), the reading reviews `03-reading/review-NN.md` (one or more, whichever ran this session), and on a test day `05-test/review.md`. These are named `review.md` and `review-NN.md` — read both forms. Capture the score and, above all, the recurring error patterns. (Listening is self-reported, not graded — there is no `04-listening/review.md`; its self-check lives in the self-report below.)
- The **writing correction** from `/grade-writing` — `lessons/session-NNN/class/03-writing/review-NN.md` (one or more, when writing ran this session instead of reading): the recurring issues plus register and structure notes.
- `weak-spots.md` (repo root) — the current weak-spot table, to churn against.
- `grammar.md` — the topic register, to record state transitions.
- `themes.md` (repo root) — the ordered theme track, to find the next theme when advancing.
- `progress/scores.csv` — to check whether the current theme's vocab scores are solid.
- `STATE.md` — the current session number `N`, per-skill levels, and the **current theme** (its name/index into `themes.md`) plus the **sessions-in-theme** count.
- The recent `lessons/session-*/recap.md` files — to rebuild the rolling root `recap.md`.
- The learner's quick self-report (ask if it wasn't already given), **including how listening and speaking each felt today** — both are self-reported, exposure-gated skills (speaking is done live throughout the session, listening is not objectively graded), so this recap is the only trace of them and the evidence `/recalibrate` reads to estimate their levels.

### Missing-input guard
If no review files exist for this session, proceed from the **self-report alone** and note in the recap that grading was skipped. Treat any other absent file as empty.

## Process
1. Read the current session number `N` from `STATE.md`. Use zero-padded ids — `session-NNN`. Everything here is indexed by **session number**, never by calendar date.
2. **Write the session recap** to `lessons/session-NNN/recap.md` — a fresh file written once this session, covering **what went well / what was hard / what to repeat / what is now solid**, grounded in the graded results above. Use frontmatter carrying the **session number `N`, the actual session duration, and the scores**. Log a one-line **listening** note and a one-line **speaking** note from the self-report (how each felt) so `/recalibrate` has the self-report trace it reads for both skills. One file per session; never overwrite another session's recap.
3. **Regenerate the rolling root recap.** Rewrite `recap.md` at the repo root as a digest of the **last 5 sessions**, newest first, built from the recent `lessons/session-*/recap.md` files: fold in this session and drop the 6th-oldest so only the latest five remain. This is what the next `/lesson` reads for recent context.
4. **Maintain `weak-spots.md`** (repo root) — the single small table: `spot | source | category | first_seen_session | last_seen_session | times_recurred | status(active/watch/cleared) | cleared_session`. The `category` is the error type (e.g. agreement, gender, case, word-order, tense/aspect, preposition, false-friend, spelling, word-choice, register — use the set that fits the target language; keep the tag short) so spots are queryable by type over time. Churn it against this session's evidence, all session-indexed:
   - **New spots** from the recurring error patterns (`/grade`) and the recurring issues (`/grade-writing`): add a row with `first_seen_session = N`, `status = active`, and assign a `category` inferred from the `/grade` (or `/grade-writing`) error pattern.
   - **Recurrence** of an already-listed active/watch spot: set `last_seen_session = N` and increment `times_recurred`; refine its `category` if the accumulated evidence now points to a better-fitting type.
   - **Clearing closes at item level** and is never one-shot: flip `active → watch → cleared` only after **≥2 spaced correct reappearances**. Record `cleared_session = N` when it reaches `cleared`.
   - **Regression:** if a previously `cleared` spot reappears (re-failed), flip `cleared → active`, increment `times_recurred`, and set `last_seen_session = N`.
   - Weak spots live **only** here — not in `STATE.md`.
5. **Record grammar transition sessions** in `grammar.md`: when this session's evidence moves a topic, advance its state and stamp the **session of the transition** (`introduced@N` → `practicing@N` → `mastered@N`). If a spaced grammar-recycle probe in the 00-check warm-up was missed, **demote** that topic to `practicing@N` and add it to `weak-spots.md`. These transition sessions are load-bearing — `/lesson` picks the least-recently-touched non-active topic from them.
6. **Advance the theme track when the current theme is solid.** The theme is the second axis (vocab + reading/writing/listening context); it never reorders grammar. Read `themes.md`, plus `STATE.md`'s current theme and sessions-in-theme. **Advance to the next theme** in `themes.md` when the current theme's vocabulary and competency are solid — signal = the theme's vocab scores are solid in `progress/scores.csv`, the theme has **stopped generating new weak spots** (no new active spots traced to it this session), and the learner handles the theme's reading/writing **without major errors**. **Guardrails (session-indexed):** stay in a theme **at least ~3 sessions** (don't flip too soon, even if it looks solid early) and **at most ~10 sessions** (force-advance to the next theme so a theme never drags). When **advancing**, set the current theme to the next entry in `themes.md` and **reset sessions-in-theme to 1**; when **staying**, **increment sessions-in-theme**. Record this in the recap (theme name, sessions-in-theme, and whether it advanced and why).
7. **Refresh `STATE.md`** (lean): the current session number, level per skill (reading/listening/writing/speaking), current focus, the **current theme** (its name/index into `themes.md`) and **sessions-in-theme** count, and the ledger pointer. **No weak spots here.**
8. **Advance the session counter idempotently:** set the next session number to `max(highest existing lessons/session-* dir, STATE N) + 1`. Re-running `/close-day` for the same session must not double-advance.
9. **Regenerate `LEARNING-PACE.md`** (repo root) when `N == 1` or `N % 3 == 0` — **throughput only**: per-segment prescribed vs completed load, the self-reported time/difficulty, and one per-segment load multiplier. It must carry **no CEFR / level / roadmap opinion** — that is `/recalibrate`'s job.
10. **Celebrate.** In both the end-of-session report and the recap, name any **cleared weak spots** with their session span (e.g. "appeared session 9, cleared session 15") and any **newly-mastered topics**, and a **theme advance** when one happened. Report-only — no achievements file.
11. **Recalibrate reminder.** If the just-closed session number `N` is a multiple of 28 (the 90-minute assessment session), remind the learner to run `/recalibrate` next. This is only a reminder — `/recalibrate` stays explicit and is never auto-invoked.
12. Commit the session's work with a clear message (e.g., `session NNN: <topic>`).

## Writes
- `lessons/session-NNN/recap.md` (this session) and the root `recap.md` (the rolling last-5 digest); `weak-spots.md` (churned); `grammar.md` (transition sessions); `STATE.md` (lean, counter advanced, current theme + sessions-in-theme updated); `LEARNING-PACE.md` (on `N == 1` or `N % 3 == 0`); one git commit.

## Why the loop matters
The weak spots churned here are what `/lesson` warms up on next time, and the session recap plus the rolling root `recap.md` are read by the next `/lesson` so it plans with continuity. The grammar transition sessions feed the spaced-recycle probe, and `LEARNING-PACE.md` feeds `/lesson`'s adaptive load. The current theme written to `STATE.md` is what the next `/lesson` builds vocab and reading/writing/listening context around — advancing it here, when the theme is solid, is what keeps the second axis moving without ever reordering grammar. Without this step, recaps are a diary nobody acts on — this is the link that turns "what I struggled with" into "what I practice next session."
