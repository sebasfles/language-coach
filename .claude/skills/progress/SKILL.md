---
name: progress
description: >
  Read-only longitudinal synthesis for the learner — a step-back view of the whole journey
  that nothing else surfaces between recalibrations. Reads the per-skill scores curve, the
  CEFR level history, the weak-spots churn, the recent session recaps (including the listening
  and speaking self-reports), STATE.md, the roadmap and themes plan, and CLAUDE.md, then reports
  per-skill trend and level, plateau detection, the top recurring error categories, on-track vs
  plan, and wins/milestones — with one actionable suggestion per plateau or sticky error. It
  CHANGES nothing: it edits no living document and writes only its own snapshot, progress.md at
  the repo root. On-demand and explicit; never auto-invoked, never part of the daily loop.
  Trigger on "how am I doing", "show my progress", "am I plateauing", "progress report".
disable-model-invocation: true
---

# /progress — read-only longitudinal synthesis

Give the **learner** a step-back view of the **whole journey** — the trends, plateaus, recurring error types, on-track-against-plan, and wins that nothing else surfaces between recalibrations. Write all learner-facing output in the **content language** defined in `CLAUDE.md`. Everything is indexed by **session number `N`** — never by calendar date.

This skill is **read-only with respect to the system's living documents**. It does **not** act, re-plan, or touch state — it only **shows**. It writes one thing: its own derived snapshot, `progress.md` at the repo root.

## Read first (explicit — don't plan from memory)
As your **FIRST action**, Read each of these files (`cat … 2>/dev/null` is fine); **treat any missing file as empty**; do not plan from memory. Ground every claim in this evidence, not a gut feeling:
- `progress/scores.csv` — the objective per-skill curve (`session, segment, skill, items, correct, pct, self_difficulty_1to5, tier`) for the graded skills: **grammar, reading, `00-check`, writing**. Read the per-skill **trend** (the slope across sessions), not a single row.
- `progress/level-history.md` — the CEFR estimate **per skill over time**, one row per `/recalibrate` run.
- `weak-spots.md` — the active/watch/cleared spots and the **`category`** column (the error **types**: agreement, gender, case, word-order, tense/aspect, preposition, false-friend, spelling, word-choice, register, …).
- the recent `lessons/session-*/recap.md` — including the **listening** and **speaking** self-report notes. These are the **only trace** of those two self-reported skills (neither is in `scores.csv`).
- `STATE.md` — the current session number `N`, the per-skill levels, and the **current theme** plus the **sessions-in-theme** count.
- `roadmap.md` + `themes.md` — the plan (the grammar intent and the theme track), to compare progress against.
- `CLAUDE.md` — the **target level** and the program **duration**; and `overview.md` for the **sessions-per-week** hours estimate (it is **not** a `CLAUDE.md` parameter) — together these give the on-track judgment.

### Missing-input guard
If the curve, the history, or the recaps don't exist yet (early in the program), say so plainly and synthesize from whatever **does** exist — never fabricate a trend. With essentially no data, report that honestly rather than inventing milestones.

## Process
Produce a report **to chat** and the refreshed `progress.md` snapshot, with these sections:
1. **Per-skill TREND & current level.** Reading / grammar / writing from the `scores.csv` **slope** plus `level-history.md`; **listening & speaking** from the recap **self-reports** (qualitative — they are not in `scores.csv`). Note the expected **asymmetry** across skills.
2. **PLATEAU detection.** Flag any skill **flat or declining** over roughly the last several sessions, and **name** it.
3. **Top recurring ERROR CATEGORIES.** Aggregate `weak-spots.md` by the **`category`** column — the top few error types, each with **active-vs-cleared** status and whether it is **trending down (improving)** or **sticky**.
4. **ON-TRACK vs plan.** Sessions done vs `roadmap.md` / `themes.md` progress and the target level / duration from `CLAUDE.md` — **ahead / on-track / behind**, honestly.
5. **WINS / milestones.** Cleared weak spots (with their **session span**, e.g. "appeared session 9, cleared session 15"), newly-mastered grammar topics, themes completed, and the current **vocab/ledger count**.
6. **One ACTIONABLE suggestion** per plateau or sticky error — **advice only**. `/progress` changes nothing; the learner can act on the advice, or run `/recalibrate` to actually re-plan.

## Writes
- `progress.md` at the **repo root only** — its own overwritten synthesis snapshot, rewritten fresh each run.
- It modifies **NO living document**. It must **not** touch `STATE.md`, `weak-spots.md`, `progress/scores.csv`, `progress/level-history.md`, `roadmap.md`, `themes.md`, `grammar.md`, `LEARNING-PACE.md`, or any recap. Read-only everywhere except its own snapshot.

## Note
`/progress` only **SHOWS** — it is read-only and on-demand, never auto-invoked, never part of the daily loop. It is distinct from:
- **`/recalibrate`**, which **ACTS** — it re-estimates CEFR per skill and edits `roadmap.md` pace, every 14th session.
- **`LEARNING-PACE.md`**, the **tactical** per-session throughput file consumed by `/lesson`.

If a plateau or sticky error here warrants a real re-plan, that is `/recalibrate`'s job — point the learner to it; don't do it here.
