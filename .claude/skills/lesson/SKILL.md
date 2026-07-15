---
name: lesson
description: >
  Generate one study session — the core per-session workflow. Use at the start of each
  study session. Reads the living docs (STATE.md, roadmap.md, grammar.md, weak-spots.md,
  LEARNING-PACE.md, progress/scores.csv, the vocabulary ledger, and the rolling recap of
  recent sessions) and produces one session scoped to the session length in CLAUDE.md: a graded
  cumulative-retrieval warm-up that opens the session, the next grammar topic with exercises, new
  vocabulary appended to the ledger, one or more reading exercises OR writing tasks (they alternate),
  a short per-session self-reported listening segment, and a test on a fixed cadence (a graded ~5–10-minute
  check every session, a 15-minute consolidation test every 7th session, and a 90-minute test every 14th
  that takes precedence over the 7th-session check).
  The current theme (from themes.md / STATE.md) drives the session's vocabulary and the context of
  the reading, writing, and listening segments; grammar stays roadmap-sequenced and independent.
  Trigger on "start today's lesson", "next session", or similar.
disable-model-invocation: true
---

# /lesson — generate one study session

Generate a single study session, scoped to the session length defined in `CLAUDE.md`. Write all learner-facing content in the **content language** defined in `CLAUDE.md`; the **target language** is the language being learned. Everything is indexed by **session number `N`** — there are no calendar dates, days, weeks, or months as cadence anywhere.

## Read first (don't plan from memory)
As your **FIRST action, Read** each of these files (`cat … 2>/dev/null` is fine); **treat any missing file as empty**; do not plan from memory:
- `STATE.md` — the current session number `N`, level per skill (reading / listening / writing / speaking), current focus, ledger pointer, and the **current theme** (its name / index into `themes.md`) plus the **sessions-in-theme** count. (Weak spots are **not** here — they live in `weak-spots.md`.)
- `roadmap.md` — the planned **grammar** topic sequence (the grammar intent). The theme **never** reorders it.
- `themes.md` (at the repo root) — the curated **theme track**: an ordered list of everyday-conversation themes, each with concrete scenarios/sub-topics, a target CEFR band, and key vocab domains. This is the **theme intent**, the second axis parallel to `roadmap.md` (the grammar intent). Read the entry for the current theme named in `STATE.md`.
- `grammar.md` — the register: each topic with state (`introduced` / `practicing` / `mastered`) and the **session number** of each transition (e.g. `introduced@N`, `practicing@N`, `mastered@N`).
- `weak-spots.md` — the active/watch/cleared weak-spot table (`spot | source | category | first_seen_session | last_seen_session | times_recurred | status | cleared_session`), where `category` is the error type (e.g. agreement, gender, case, word-order, tense/aspect, preposition, false-friend, spelling, word-choice, register).
- `LEARNING-PACE.md` — throughput only: per-segment prescribed vs completed load, self-reported time/difficulty, and a per-segment load multiplier. (No CEFR/level opinion — that is `/recalibrate`'s job.)
- `progress/scores.csv` — append-only score history (`session, segment, skill, items, correct, pct, self_difficulty_1to5, tier`).
- `vocab/ledger.csv` — what vocabulary already exists.
- `CLAUDE.md` — the session length, the per-session vocabulary cap, `LISTENING_RESOURCES`, `LISTENING_SUPPORT_LANGUAGE` (defaults to the content language), the per-language pronunciation note, and the rest of the plan parameters.
- `recap.md` (at the repo root) — the rolling digest of the last 5 sessions, for recent context.
- the previous session's recap — `lessons/session-{N-1}/recap.md` — for detail on what was hard or left unfinished.

## Cold start (N == 1, or any input absent)
On the **first session** (or whenever an input file is absent), **skip the previous-recap read**, treat absent docs as empty, and don't fabricate history:
- Replace the `00-check` retrieval warm-up with a short **level-placement diagnostic** (the warm-up is conditional on weak spots and prior material actually existing).
- `lesson.md` **also carries the first-run orientation**: the loop in four steps (`/lesson` → answer → `/grade` + `/grade-writing` → `/close-day`), one honest-expectations sentence, and a deliberately **light, confidence-building** first session.

## Theme axis (the second axis, orthogonal to grammar)
The **current theme** (from `STATE.md`, looked up in `themes.md`) is a **second axis, orthogonal to grammar**. It drives **two things only**: the session's new **vocabulary** (the bulk of it) and the **context/topic** of the reading (`03-reading`), writing (`03-writing`), and listening (`04-listening`) segments — all set in the current theme's situations — plus what the learner practices in live speaking. **Grammar rides its own track:** `02-grammar` follows `roadmap.md` by difficulty and is **independent of the theme** — a theme **never** reorders grammar.

**INPUT vs OUTPUT rule (critical):**
- **INPUT** — `03-reading` + `04-listening`: the content is **on the current theme** and **MAY contain grammar above the current roadmap point** — that is welcome (comprehensible input, i+1). **Gloss** such structures briefly ("this is X — covered later; just get the gist"), do **not** drill them, and keep the text overall comprehensible (not far above level).
- **OUTPUT** — `03-writing` + live speaking: stays **within the grammar taught so far** (roadmap up to now) plus the theme vocab. **Never** require the learner to produce a structure not yet taught; a writing task on the theme must be solvable with current grammar.

**Recalibrate signal:** if an advanced structure **recurs** in the input across sessions, that is a signal for `/recalibrate` to consider pulling it **forward** in `roadmap.md`. Note it where natural, but don't act on the roadmap here — that is `/recalibrate`'s job.

## Assessment item formats (apply when building every exercise/test)
Apply the **assessment item-format policy in `CLAUDE.md`** when building every exercise and test. Brief per-segment format hints:
- `00-check` (every session) → **fast:** short cloze + a couple of diagnostic MC.
- `02-grammar` (every session) → **production-biased:** cloze, transformation, translation; MC only for confusable contrasts.
- `03-reading` / `04-listening` → **comprehension MIX:** MC/TF for gist, open short-answer for detail.
- `03-writing` → **open production** (holistic; graded by `/grade-writing`).
- `05-test`, 7th session (15 min) → **balanced mix, production-heavy.**
- `05-test`, 14th session (90 min) → **exam-like:** sections per skill, multi-format.

## Session-counter reconciliation
Cross-check `STATE.md`'s `N` against the highest existing `lessons/session-*` directory. If they disagree, or if `lessons/session-NNN/` already has content, **warn before writing** into a non-empty session directory. Use zero-padded ids — `session-NNN`.

## Process
1. Read the current session number `N` from `STATE.md`. Let the previous session's recap and the rolling `recap.md` shape `00-check` and pacing — carry forward what was hard or left unfinished. Add a one-line **"last time"** recall to `lesson.md`, drawn from the recap.
2. **00-check (every session, ~5–10 min) — the graded cumulative-retrieval warm-up that opens the session.** This is the warm-up: a graded retrieval of **PRIOR material plus active weak spots**, **not** today's new topic — and this is where recycling happens, so don't skip it. Build it from `weak-spots.md`, **ordered by `times_recurred` (most-churned first)** (and it **MAY** group or prioritize by the `category` column), plus two fixed injections:
   - **Spaced grammar recycle:** inject the single **least-recently-touched non-active topic** (by the transition session recorded in `grammar.md`) as a 2–3 item probe. (On error, `/close-day` demotes it to `practicing` and it re-enters `weak-spots.md` — this is the consumer that makes the grammar transition sessions load-bearing.)
   - **Escalation:** a re-failed previously-cleared weak spot is routed into the **standard grammar machinery** — create an **extra** `02-grammar/<topic-slug>/` folder for the regressed topic that session, with its normal `exercise-NN.md` + fillable `answers-NN.md` + `/grade` `review-NN.md` trio, so it has a real path, a worksheet, and the existing readers handle it. It is just another `02-grammar` topic folder that session, not just another check line.
   Keep items **fast** (short cloze + a couple of diagnostic MC) per *Assessment item formats*. Write it to `lessons/session-NNN/class/00-check/check.md`, and **generate the fillable worksheet** `00-check/answers.md` (the check items reproduced with blank slots — the learner just fills them in); `/grade` writes `00-check/review.md`; `/close-day` folds the result into weak-spots churn. On a **cold start** (`N == 1`), replace `00-check` with the level-placement diagnostic instead.
3. **02-grammar — the backbone (every session).** Teach the next topic in `roadmap.md` that `grammar.md` marks as still owed (not yet `mastered`), with worked examples and exercises. Grammar is **roadmap-sequenced and independent of the theme** — pick the next owed topic by difficulty, never by the theme. Make exercises **production-biased** (cloze, transformation, translation; MC only for confusable contrasts, with diagnostic distractors) per *Assessment item formats*. For each grammar topic taught today create `lessons/session-NNN/class/02-grammar/<topic-slug>/`: write today's teaching to `grammar.md` inside it (linking into the cumulative `grammar/<topic>.md` reference), the exercise tasks to `exercise-01.md`, `exercise-02.md`, …, and create or extend the cumulative `grammar/<topic>.md` reference page. **Generate the fillable worksheet** `answers-NN.md` **beside each `exercise-NN.md`** (the exercise items reproduced with blank slots for the learner to fill); `/grade` writes `review-NN.md` next to it. Grammar always keeps advancing the roadmap, even on an asymmetric-allocation day.
4. **01-vocab (every session).** Introduce new items (see the vocab cap below) — **mostly current-theme vocab (the bulk)**, drawn from the theme's scenarios and key vocab domains in `themes.md`, **plus some high-frequency general words** so exposure isn't narrowed to only the theme. All of it stays within the shared per-session cap. Write them as a human-readable diff to `lessons/session-NNN/class/01-vocab/new-words.md`, **and also** append each as a row to the canonical `vocab/ledger.csv` in the ledger's format, following the target-language vocabulary conventions in `CLAUDE.md` (include the optional IPA column when the ledger has one), tagged with the session (e.g., `session-NNN`). **Dedup per the vocabulary/ledger convention in `CLAUDE.md`:** the ledger's stable first field is the canonical headword **with** its article (e.g. `das Haus` for gendered languages); the dedup key is that canonical first field compared **case-insensitively (lowercased)** — the article is part of the canonical form and is **not** stripped. Don't append an item whose canonical first field already matches a ledger row under that key.
5. **Rotating main course — 03-reading and 03-writing ALTERNATE (they share slot `03`).** Run **exactly one** of the two per session — never both. The slot can hold **one or more** exercises/tasks; a single one is often too little. **Alternation is driven by "track which ran last"** — the single authoritative rule, robust to test-only sessions that skip slot 03: run whichever did **not** run last. **Cold-start seed:** session 1 runs **03-reading** (input first). A **test-only session (14th) does NOT consume the alternation** — the slot is skipped, so the next non-test session continues from whichever ran last. (Parity of `N` is only an illustrative aside, not the rule.)
   - **03-reading** (INPUT): **one or more** reading exercises in `lessons/session-NNN/class/03-reading/`, each a passage plus its comprehension questions in `exercise-NN.md` (`exercise-01.md`, `exercise-02.md`, …). Build the questions as a **comprehension mix** (MC/TF for gist, open short-answer for detail) per *Assessment item formats*. **Generate the fillable worksheet** `answers-NN.md` beside each (the comprehension questions reproduced with blank answer slots); `/grade` writes `review-NN.md` next to it. The reading material **varies between a conversation/dialogue and a continuous prose text** — rotate across sessions for register variety (spoken-style dialogue vs written prose). Set the passage **in the current theme's situations**; as input it **may carry grammar above the roadmap point** — **gloss** such structures briefly, don't drill them, and keep it overall comprehensible (i+1).
   - **03-writing** (OUTPUT): **one or more** writing tasks in `lessons/session-NNN/class/03-writing/`, each prompt in `task-NN.md` (`task-01.md`, `task-02.md`, …) — **open production** (graded holistically by `/grade-writing`) per *Assessment item formats*. **Generate the fillable worksheet** `submission-NN.md` beside each (the prompt reproduced with a blank area to write); `/grade-writing` writes `review-NN.md` next to it. Frame the task as a concrete **case / scenario within the current theme** — a real situation the learner responds to in writing (e.g. theme=restaurant → "write a short message complaining that a dish arrived cold and asking for a fix") — and **vary the scenario across sessions**. This is **in addition to** the register variety: the writing **also varies between a conversation/dialogue and a continuous prose text** — rotate across sessions (spoken-style dialogue vs written prose). Set the task **in the current theme's situations**, but keep it **within the grammar taught so far** (roadmap up to now) plus theme vocab — **never** require a structure not yet taught; the task must be solvable with current grammar.
   - **Interleaving:** compose the reading exercises and writing tasks to deliberately **reuse active weak-spot grammar** and the **last 1–2 sessions' vocab**.
6. **04-listening (short per-session staple, ~10–15 min) — INPUT, SELF-REPORTED.** Listening, like speaking, is a **self-reported skill: it is NOT graded by `/grade` and yields NO `progress/scores.csv` row and NO `/grade` review file.** The comprehension questions are for the learner's own **active-listening self-check**. Since you can't watch or hear a clip, write a **repeatable protocol** to `lessons/session-NNN/class/04-listening/task.md`. Prefer **transcript/subtitle-bearing sources** — with `LISTENING_SUPPORT_LANGUAGE`, dual-subtitle **Easy Languages** is the default; otherwise a level-appropriate clip from `LISTENING_RESOURCES` in `CLAUDE.md`. Steer the clip choice toward the **current theme's situations**; as input it **may carry grammar above the roadmap point** — **gloss** such structures briefly, don't drill them, and keep it overall comprehensible (i+1). The task is a gist-and-detail **comprehension mix** (3–5 questions: MC/TF for gist, open short-answer for detail, per *Assessment item formats*) plus noting new words. **Offline fallback:** if the learner has no listed source, have them name any clip they have, and emit a **generic gist+detail comprehension plus a short dictation micro-task** that needs no specific source. **Generate the fillable worksheet** `04-listening/answers.md` (the comprehension questions reproduced with blank answer slots, a **"new words" slot**, **and a "how it felt / self-rated comprehension" field**); new words still flow to `/harvest`. The listening level is driven by `STATE.md`'s per-skill listening level (set by `/recalibrate` from the `/close-day` self-report), not by `scores.csv`.
7. **05-test (cadence by `N`, explicit durations).** **Precedence:** when `N` is a multiple of 14, the **90-minute standalone test TAKES PRECEDENCE** over the every-7th-session 15-minute test — the 14th is test-only and the 15-minute rule does **not** also apply that session (14 is itself a multiple of 7, so check the 14th case first).
   - every 7th session (that is **not** also a 14th) → a **15-minute** consolidation test to `lessons/session-NNN/class/05-test/test.md`; a **balanced mix, production-heavy** (per *Assessment item formats*); make the taught content lighter so the total stays within the session length.
   - every 14th session → a **90-minute (1h30)** test to `lessons/session-NNN/class/05-test/test.md` as a **standalone block** — **exam-like: sections per skill, multi-format, mirroring a real proficiency test** (per *Assessment item formats*); test only, no new teaching, and it runs longer than a normal session. The only `class/` segment that day is `05-test/`.
   On a test day, **generate the fillable worksheet** `05-test/answers.md` (the test items reproduced with blank slots); `/grade` writes `05-test/review.md`. **Never combine a full lesson and a large test in one session** — that blows the time budget. (The every-session ~5–10-minute check is `00-check`, not a test.)
8. Write the session plan/overview to `lessons/session-NNN/lesson.md` — the `00-check` notes, what is covered, the time budget, **the per-segment answer-file the learner fills in** (see below), and links to the segments created above. It opens with a short **"why today"**: name the **current theme** (the situation you're building toward), tie `00-check` to the specific weak spots, name the new grammar topic and why it is next, and connect to the roadmap goal — plus the one-line **"last time"** recall. **`lesson.md` is always written**, regardless of which segments exist. On a 14th-session test day, `lesson.md` states the day is the 90-minute assessment (what it covers, no new material) and that the only `class/` segment is `05-test/`.

**Segment order and numbering are fixed:** `00-check` → `01-vocab` → `02-grammar/<topic-slug>` → `03-reading` *or* `03-writing` (alternating, exactly one per session — they share slot `03`) → `04-listening` → `05-test`. The **spine every session** is `00-check` (the graded retrieval warm-up) + `01-vocab` + `02-grammar` + `04-listening`; reading and writing alternate in slot `03`; the test segment exists only on cadence (7th and 14th). **Scale every segment's depth to the session length in `CLAUDE.md`:** listening stays short (~10–15 min) as the per-session staple, and the heavier academic segments carry the bulk and may rotate emphasis session to session so the total stays within the session.

## Learner answer-file convention — GENERATE fillable worksheets (surface in `lesson.md`)
`/lesson` does **not** merely declare *where* the learner writes — it **creates each answer file as a ready-to-fill worksheet**: the items/questions reproduced with **blank answer slots**, so the learner just fills them in (this makes "fill-in" literal). The learner **fills** these; they do **not** create files or guess paths. The task/prompt files (`check.md`, `02-grammar exercise-NN.md`, `03-reading exercise-NN.md`, `03-writing task-NN.md`, `04-listening task.md`, `05-test test.md`) stay as the prompts; the `answers-*` / `submission-*` files are their fillable companions, and `/grade` / `/grade-writing` read the filled worksheet. Generate, per segment:
- `00-check/answers.md` — the check items with blank slots.
- `02-grammar/<topic-slug>/answers-NN.md` — the exercise items with blanks, one beside each `exercise-NN.md`.
- `03-reading/answers-NN.md` — the comprehension questions with blank answer slots, one beside each reading `exercise-NN.md`.
- `03-writing/submission-NN.md` — the prompt referenced with a blank area to write (free production), one beside each `task-NN.md`.
- `04-listening/answers.md` — the comprehension questions with blanks **plus a "new words" slot and a "how it felt / self-rated comprehension" field** (self-reported; not graded by `/grade`).
- `05-test/answers.md` (on a test day) — the test items with blank slots.

## Adaptive difficulty
`scores.csv`-driven adaptive difficulty applies to the **objectively-graded segments only** — grammar + reading + `00-check` + writing (holistic via `/grade-writing`). Read the trailing ~5 rows **per skill** from `progress/scores.csv` plus the per-segment **load multipliers** in `LEARNING-PACE.md`:
- **3 consecutive ≥90%** on a segment → **bump that segment's level**.
- **any <70%** → **ease that segment** and **force a `00-check` retrieval probe** on it.

**Listening is exempt** (it is self-reported, not in `scores.csv`): its allocation and difficulty are driven by `STATE.md`'s per-skill **listening level** (set by `/recalibrate` from the `/close-day` self-report), not by `scores.csv`.

## Asymmetric allocation
When `STATE.md` shows a skill (especially **listening**) lagging the others by a band, **lift its time floor** (≥10–15 min, more when it is the bottleneck) and **trim — not zero — the over-developed academic segments** that day. Grammar always keeps advancing the roadmap regardless.

## Vocab cap
~15–30 new items is a **per-session TOTAL shared across `/lesson` introductions AND `/harvest`** — harvest tops up *toward* the cap, never on top of it. It **flexes down** when the learner reports a large Anki review backlog. Route the count through `LEARNING-PACE.md`.

## Speaking
There is **no speaking segment to generate** and **no `/speak` skill** — speaking is done **live** throughout the session. It is still tracked as a skill level in `STATE.md`; `/close-day` asks the speaking self-report. Do **not** create a speaking segment here.

## Writes
- `lessons/session-NNN/lesson.md` (always);
- `lessons/session-NNN/class/00-check/check.md` plus the fillable worksheet `00-check/answers.md`;
- `lessons/session-NNN/class/01-vocab/new-words.md` plus new rows appended to `vocab/ledger.csv`;
- per grammar topic, `lessons/session-NNN/class/02-grammar/<topic-slug>/grammar.md` and `exercise-NN.md` plus the fillable worksheet `answers-NN.md` beside each, plus a created/extended cumulative `grammar/<topic>.md`;
- on a reading session, `lessons/session-NNN/class/03-reading/exercise-NN.md` (one or more) plus the fillable worksheet `answers-NN.md` beside each; on a writing session, `lessons/session-NNN/class/03-writing/task-NN.md` (one or more) plus the fillable worksheet `submission-NN.md` beside each;
- `lessons/session-NNN/class/04-listening/task.md` plus the fillable worksheet `04-listening/answers.md` (with a "new words" slot and a "how it felt / self-rated comprehension" field; self-reported, not graded);
- on cadence (7th / 14th session), `lessons/session-NNN/class/05-test/test.md` plus the fillable worksheet `05-test/answers.md`.

## Out of scope
Grading is `/grade` and `/grade-writing` (they also append a row to `progress/scores.csv`). Maintaining `weak-spots.md`, the recaps, the grammar transition sessions, `LEARNING-PACE.md`, and advancing the counter is `/close-day`. Re-estimating CEFR and adjusting roadmap pace is `/recalibrate`. Don't do those here.
