# Language Coach Kit — for Claude Code

A starter kit that turns Claude Code into a personal, self-study coach for **any** language. You answer a few questions once; it builds you a personalized study plan and runs your day-to-day learning — lessons, vocabulary, writing correction, tests, and progress tracking — all in a git repo you own.

It works for any target language and any explanation language: you choose both when you set up.

---

## Requirements

- **Claude Code** (on a paid Claude plan).
- **git** — your learning lives in a version-controlled repo.
- **[Anki](https://apps.ankiweb.net/)** for vocabulary review (free on desktop and Android; paid on iOS). The kit feeds Anki; it doesn't replace it.

---

## Quick start

1. **Clone this repo.** It becomes your personal learning repo.

2. **Run `/new-plan` in Claude Code.** It asks a few questions:
   - **Required:** the language to learn, the language you want explanations/corrections in, and how long one study session is.
   - **Optional:** total program duration, and your target level (CEFR, e.g. B2).

   It writes your personalized `overview.md`, **builds the scaffold** — `CLAUDE.md`, the living documents, and the folder structure — and **generates `roadmap.md`** (your grammar sequence) and **`themes.md`** (your situational theme track), all in one go. (The coaching skills already ship with the kit.)

3. **Start learning.** Run `/lesson` to begin each session and `/close-day` to end it.

---

## The session loop

- **`/lesson`** — start a session. Every session sits in a current theme (the real-life situation you're building toward), which sets its vocabulary and the context of its reading, writing, and listening. It opens with a graded ~5–10 minute retrieval warm-up on your weak spots and prior material, then the next grammar topic with exercises, ~15–30 new vocabulary words (mostly on the theme, logged for Anki), and a short listening task (an Easy Languages clip at your level, or a level-appropriate podcast). Reading and writing alternate — exactly one of them per session, each holding one or more exercises and varying between a conversation/dialogue and a continuous prose text for register variety. A 15-minute test runs every 7th session; a 90-minute test every 14th. The exercises and tests are mostly **fill-in / production** — you produce the answer (fill a blank, transform a sentence, write a short reply), with multiple-choice used selectively where it's the right tool (to contrast confusable forms, or to check that you understood a reading or listening passage). Alongside each task, `/lesson` generates a ready-to-fill **answer worksheet** — the questions reproduced with blank slots; you open it and fill in your answers, no files to create or paths to guess. Speaking you do live, throughout the session, on your own — it isn't a generated segment, but your progress in it is still tracked.
- Do the work, then get feedback: **`/grade`** for grammar and reading answers, **`/grade-writing`** for your writing. Listening, like speaking, is self-assessed — you check how it felt and how much you understood, rather than getting an objective score.
- **Practicing speaking on your own.** Since speaking is live and ungraded, two habits make it self-correcting: **shadow** the session's Easy Languages clip — play it and mimic the speaker out loud, copying their rhythm and prosody; and **record yourself and compare** against a model — check single words on [Forvo](https://forvo.com/) (native recordings), hear a word across many real clips on [YouGlish](https://youglish.com/), or use Google Translate's TTS for a quick reference.
- **`/close-day`** — end the session. It maintains your `weak-spots.md`, writes the session's `recap.md`, refreshes the rolling root `recap.md` digest of your last 5 sessions, regenerates the `LEARNING-PACE.md` pace file, updates your progress, advances you to the next theme when the current one is solid, and commits. On every 14th session it reminds you to run `/recalibrate` next.
- **`/recalibrate`** re-estimates your level per skill, adjusts the roadmap pace, and logs a row to `progress/level-history.md` — it runs every 14th session.
- **`/progress`** — run it whenever you want a step-back view of your whole journey: per-skill trend, plateaus, top error types, and on-track vs plan. It only reads your data and writes a `progress.md` snapshot — it never changes your plan (that's `/recalibrate`). It isn't part of the daily loop; reach for it on demand.

---

## What's in the kit

| Skill | Does |
|---|---|
| `/new-plan` | One-time setup: from your answers, generates your `overview.md`, the scaffold, the grammar `roadmap.md`, and the situational `themes.md`. |
| `/lesson` | Generates one study session, scoped to your session length. |
| `/close-day` | Recaps the session, updates progress, commits. |
| `/grade` | Grades a test or exercise set (grammar and reading), with the *why* of each error. |
| `/grade-writing` | Holistic writing correction + a fully corrected version. |
| `/recalibrate` | Re-estimates level per skill and adjusts the roadmap pace; runs every 14th session. |
| `/progress` | Read-only progress report you can run anytime — per-skill trend, plateaus, top error types, on-track vs plan — written to a `progress.md` snapshot. |
| `/harvest` *(optional)* | Adds words you flagged in a reading to your vocabulary list. |

Skills live in `.claude/skills/`. Their full specs are the individual `SKILL.md` files.

---

## How it's organized

A few **living documents** are the brain of the system, all read by `/lesson`:

- `STATE.md` — where you are right now (level per skill, current session, current focus, and the current theme with how many sessions you've spent in it).
- `roadmap.md` — the **grammar** track: the topic sequence by difficulty (what grammar is next).
- `themes.md` — the **theme** track: the situational topics you build toward (food, travel, work, appointments…), curated by how often they come up in real conversation and by level. You don't pick them — they're the high-utility defaults, and you advance to the next one adaptively, once the current theme's vocabulary and competency are solid (and never sooner than a few sessions or later than about ten).
- `grammar.md` — which topics you've covered and how solid each is, with the session each one was introduced, practiced, and mastered.
- `recap.md` — a rolling digest of your last 5 sessions, regenerated each session by `/close-day`. This is what `/lesson` reads for recent context.
- `weak-spots.md` — the small table of things you keep getting wrong, with how often each has recurred and whether it's active, on watch, or cleared.
- `LEARNING-PACE.md` — your throughput per segment (prescribed vs. completed load, self-reported time and difficulty), regenerated by `/close-day` on session 1 and every 3rd session.
- `progress/scores.csv` — an append-only log of every graded segment; `progress/level-history.md` — one row per `/recalibrate` run.
- `vocab/ledger.csv` — your running vocabulary list (with an optional IPA pronunciation column).

**Two parallel tracks run the plan.** `roadmap.md` and `themes.md` are orthogonal: a theme never reorders your grammar. Grammar advances on its own track, by difficulty. The theme rides on top — it supplies the bulk of each session's new **vocabulary** and sets the **context** of what you read, write, and listen to (and what you practice speaking). So a "food" theme fills the reading, writing, listening, and vocab with food situations while the grammar segment keeps following the roadmap wherever it happens to be.

**What you read and hear vs. what you write and say.** Reading and listening (the *input*) are on the current theme and may use grammar **above** where you are on the roadmap — that's deliberate (it keeps you a notch ahead); such structures are briefly glossed ("covered later — just get the gist"), not drilled, and the text stays comprehensible overall. Writing and speaking (the *output*) stay **within** the grammar you've actually been taught so far, plus the theme vocab — you're never asked to produce a structure you haven't learned yet.

**Everything for one session lives in one folder**, `lessons/session-NNN/`:

- `lesson.md` — the session plan (what's covered, time budget, links to the segments).
- `recap.md` — this session's recap, written by `/close-day`.
- `class/` — the materials and your work, in numbered segments that always follow this order: `00-check/` (the graded retrieval warm-up), `01-vocab/`, `02-grammar/<topic>/`, then either `03-reading/` or `03-writing/` — they share one slot and alternate, exactly one per session, each holding one or more exercises and varying between a conversation/dialogue and a continuous prose text — `04-listening/` (every session), and `05-test/` only on test sessions. `/lesson` scales each segment to fit your session length and decides which to create. Each segment with answers also gets a ready-to-fill **worksheet** next to its prompt (an `answers-*.md`, or a `submission-*.md` for writing) — the items reproduced with blank slots for you to fill in; that's the file `/grade` and `/grade-writing` read. Speaking isn't a numbered segment — you do it live, throughout the session.

Across sessions, `grammar/<topic>.md` is the cumulative **reference** library (the explanations each session's grammar segment links into). Your personalized `overview.md` documents the whole setup.

---

## Vocabulary & Anki

`/lesson` appends new words to `vocab/ledger.csv`. You import that file into Anki to review them. Two things worth knowing:

- **Re-importing is safe.** Anki matches on the first field, so importing the ledger again only adds new words — it never duplicates or resets the ones you already have.
- **Your progress lives in Anki, not the file.** What you know well and what you're struggling with is Anki's, so regenerating or re-importing the ledger never erases your review history.

The ledger may carry an optional **IPA** column for pronunciation, alongside a per-language pronunciation note in `CLAUDE.md`.

Keep the CSV as **UTF-8** so accents and special characters survive.

---

## How it stays flexible

Everything specific to *your* plan — the language, the level, the session length, the vocabulary conventions — lives in `CLAUDE.md`. The skills read those values from there, so the same skills work unchanged for any language. That's why they ship pre-built: the variable part is your `CLAUDE.md`, the invariant part is the skills.

All scaffolding (skills, file fields) is in English; everything you actually read while learning — explanations, corrections, prompts — comes in the content language you chose, with your target language as the language being learned.
