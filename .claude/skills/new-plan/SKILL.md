---
name: new-plan
description: >
  Bootstrap a new self-study language-learning project from the bundled
  overview-template.md. Use this once, at the very start of a fresh repo. It collects
  the learner's parameters — target language, content language, and session length
  (required), plus optional program duration, target level, and a sessions-per-week
  hours estimate — then writes overview.md, builds the full project scaffold
  (CLAUDE.md and the blank living docs), and generates roadmap.md (a CEFR-tiered,
  session-sequenced grammar plan) and themes.md (a curated, frequency-ordered theme
  track). Trigger when the user says things like "start a new
  language plan", "set up a learning repo", or "generate my overview".
disable-model-invocation: false
---

# /new-plan — generate a personalized `overview.md`, scaffold, `roadmap.md`, and `themes.md`

You are bootstrapping a new self-study language-learning project. In one run you generate a personalized `overview.md` from the bundled template, **build the project scaffold** from it, and **generate `roadmap.md` and `themes.md`** (PHASE 2). You do **not** create any other skills — the learning skills already ship with this kit and never change per plan — and you do **not** generate lessons or vocabulary (those come later, via `/lesson`).

Grammar and themes are **two orthogonal axes**. `roadmap.md` is the **grammar intent** (what to teach, sequenced by difficulty); `themes.md` is the **theme intent** (the everyday-conversation contexts that drive each session's vocabulary and the topic of reading/writing/listening). A theme never reorders grammar — grammar rides its own track and the theme rides on top supplying vocab + context.

Everything in this kit is indexed by **session number** (`N`); there are no calendar dates, days, or weeks as cadence. `SESSIONS_PER_WEEK` survives only as an optional hours-estimate input for `overview.md` — no skill uses it for numbering.

## Steps

1. **Read the template.** Open `${CLAUDE_SKILL_DIR}/overview-template.md` (it lives next to this skill). It defines every section the output must contain, marks parameters with `{{double braces}}`, and marks filler instructions with `[square brackets]`.

2. **Collect the parameters.** If the learner hasn't already given them, ask — concisely, in a single round:

   **Required (do not proceed without these):**
   - `TARGET_LANGUAGE` — the language to learn.
   - `CONTENT_LANGUAGE` — the language explanations, corrections, and prompts should be written in.
   - `SESSION_LENGTH` — how long one study session is.

   **Optional (ask, but offer the default and don't block on them):**
   - `PROGRAM_DURATION` — total length of the plan. Default: open-ended.
   - `TARGET_LEVEL` — desired level, ideally CEFR. Default: B2.
   - `SESSIONS_PER_WEEK` — sessions per week or the weekly pattern. Used **only** to estimate total available hours for `overview.md`; it is never a standing parameter and no skill uses it for numbering (everything is indexed by session `N`). If not given, ask once, otherwise assume a sustainable default and say so.

   Also propose or ask for a short `REPO_NAME`.

3. **Fill the template into `overview.md`:**
   - Substitute every `{{PARAMETER}}`.
   - **Specialize the language-specific guidance for `TARGET_LANGUAGE`:** the vocabulary conventions (gendered → nouns with article + plural; cased → note case behavior; tonal → mark tone; verbs → record the unpredictable forms) and the broad grammar arc from beginner to the target level. You may use web search to verify difficulty and typical hours if unsure.
   - **Specialize the listening sources for `TARGET_LANGUAGE`** (same as you specialize the vocabulary conventions): the Easy Languages series for that language (Easy German, Easy Spanish, Easy French, Easy Italian, etc.) plus level-appropriate podcasts and graded listening. These feed the per-session `04-listening` segment, so name concrete, real sources for the target language. Note the **listening support language** (the default is the content language — with a dual-subtitle source like Easy Languages this makes dual subtitles the default).
   - **Write a per-language pronunciation note for `TARGET_LANGUAGE`:** the sounds and spelling-to-sound traps that matter for a `CONTENT_LANGUAGE` speaker. (There is no pronunciation drill skill; this note plus the optional IPA column in the ledger carry pronunciation.)
   - **Write the honest-expectations and hours sections truthfully.** Estimate the guided hours typically needed to reach `TARGET_LEVEL` in `TARGET_LANGUAGE` for a `CONTENT_LANGUAGE` speaker — the closer the two languages, the fewer hours. If total available hours can be computed (`PROGRAM_DURATION` × `SESSIONS_PER_WEEK` × `SESSION_LENGTH`), compare it and state plainly whether the target is comfortable, tight, or a stretch. Always note the asymmetric shape of progress (receptive skills and grammar lead; listening at native speed and speaking lag) and that hours — not cleverness — gate the exposure-bound skills.
   - **Apply the language rule:** all scaffolding stays in English; all learner-facing content is written in `CONTENT_LANGUAGE`; the target language is `TARGET_LANGUAGE`.
   - Replace every `[bracketed instruction]` with real, specialized content. Never copy a bracket or a `{{placeholder}}` verbatim into the output.

4. **Write the result** to `overview.md` at the repo root.

5. **Build the scaffold** from the `overview.md` you just wrote — its §7 lists exactly what to create. Use the **content language** for any learner-facing field labels; keep field names, headers, and structure in English. Create:

   - **`CLAUDE.md`** — the §2 teaching principles, the plan parameters (target language, content language, session length, target level, duration), the target-language vocabulary conventions (including the **ledger dedup convention** below), the target-language **`LISTENING_RESOURCES`** (the Easy Languages series plus level-appropriate podcasts / graded listening, specialized for the target language), **`LISTENING_SUPPORT_LANGUAGE`** (default = the content language; with a dual-subtitle source like Easy Languages this makes dual subtitles the default), a **per-language pronunciation note** (the sounds/spelling-to-sound traps that matter for the target language), and "read `STATE.md` first." Add a **themes teaching principle**: themes (`themes.md`) drive the session's vocabulary and the context/topic of reading, writing, and listening, while grammar stays roadmap-sequenced and **independent** — a theme never reorders grammar. Advanced grammar **may** appear in **INPUT** (reading/listening) as comprehensible input — gloss it briefly, do not drill it — but **OUTPUT** (writing/speaking) stays within the grammar taught so far. Add a **graded-vs-self-reported principle** (this is the single authoritative statement of it): the **objectively-graded** segments are grammar, reading, the `00-check`, and writing (graded holistically by `/grade-writing`) — only these produce `progress/scores.csv` rows and `/grade` review files. **Listening and speaking are self-reported skills**: they are **not** objectively graded, produce **no** `scores.csv` row and **no** `/grade` review file; their levels come from `/close-day`'s self-report (estimated by `/recalibrate`), and `/lesson` drives listening's allocation/difficulty from `STATE.md`'s per-skill listening level, not from `scores.csv`. (Listening new words still flow to `/harvest`.) Add the **ledger dedup convention** (the single source both `/lesson` and `/harvest` cite): in `vocab/ledger.csv` the stable first field is the **canonical headword WITH its article** for gendered languages (e.g. `das Haus`), exactly as the vocabulary conventions record it; dedup matches on that first field **case-insensitively (lowercased)** — the article is **part** of the canonical form and is **never stripped**. Add an **assessment item-format principle** — this `CLAUDE.md` is the authoritative home of the policy (`/lesson`, `/grade`, and the overview template only point here); it is applied by `/lesson` when it builds exercises/tests and by `/grade` when it grades: assessments **default to PRODUCTION / fill-in** — cloze, transformation, short open answer, and (sparingly) `CONTENT_LANGUAGE`→`TARGET_LANGUAGE` translation — because recall beats recognition (the testing effect) and the kit can afford it (the LLM grader has no rigid answer key, so produced answers are gradable). **Multiple-choice / true-false / matching are a deliberate MINORITY**, used only where genuinely best: (a) **discriminating confusable forms** (e.g. ser/estar, der/die/das, por/para, tense pairs); (b) **reading/listening comprehension gist** (isolating understanding from production); (c) **early scaffolding / context-completion** (MC-cloze when full production is still too hard); (d) **fast diagnostics in the 00-check**. Every MC/TF must use **diagnostic distractors** — each wrong option maps to a specific real misconception, never a lazy item with one obvious answer; and vary production types rather than over-relying on translation. **Format by layer:** 00-check → fast (short cloze + a couple of diagnostic MC); 02-grammar → production-biased (cloze, transformation, translation; MC only for confusable contrasts); 03-reading / 04-listening → comprehension MIX (MC/TF for gist, open short-answer for detail); 03-writing → open production; 05-test 7th session → balanced, production-heavy; 05-test 28th session → exam-like (sections per skill, multi-format, mirroring a real proficiency test). The learning skills read these values from `CLAUDE.md`, so they must be present and accurate. (`SESSIONS_PER_WEEK` is **not** a `CLAUDE.md` parameter — it is only an optional `/new-plan` hours-estimate input; no skill uses it for numbering.)

   - **`STATE.md`** — a concrete, sectioned template (no progress data): a **current session** field (`N: 1`); a **level per skill** block (reading / listening / writing / speaking); a **current focus** line; a **current theme** field (the theme name / index into `themes.md`, set to theme 1) and a **sessions-in-theme** field (`0`); and a **ledger pointer** (the last session-tag written to `vocab/ledger.csv`). Weak spots do **not** live here — they live in `weak-spots.md`.

   - **`grammar.md`** — the register, empty but with its convention stated: each topic carries a state (`introduced` / `practicing` / `mastered`) **and the session number of each transition** (e.g., `introduced@N`, `practicing@N`, `mastered@N`).

   - **`themes.md`** (repo root) — the curated **theme track** (the theme intent, parallel to `roadmap.md`). Its content is generated in PHASE 2; if you scaffold it here, leave it as a placeholder to be filled in PHASE 2.

   - **`recap.md`** (repo root) — a placeholder for the rolling digest of the last 5 sessions, regenerated by `/close-day`.

   - **`weak-spots.md`** — a single small table with this schema (header row only): `spot | source | category | first_seen_session | last_seen_session | times_recurred | status | cleared_session`, where `category` is the short error-type tag (e.g. agreement, gender, case, word-order, tense/aspect, preposition, false-friend, spelling, word-choice, register — use the set that fits the target language) and `status` is one of `active` / `watch` / `cleared`.

   - **`LEARNING-PACE.md`** — the throughput register (schema only, no data): per-segment **prescribed vs. completed** load, self-reported time/difficulty, and one **per-segment load multiplier**. It carries **no** CEFR / level / roadmap opinion (that is `/recalibrate`'s job). Regenerated by `/close-day` on session 1 and every 3rd session; read by `/lesson` and `/recalibrate`.

   - **`progress/scores.csv`** — append-only, header row only: `session,segment,skill,items,correct,pct,self_difficulty_1to5,tier`. Written by `/grade` and `/grade-writing`.

   - **`progress/level-history.md`** — append-only, one row per `/recalibrate` run (session `N`, CEFR per skill, what changed and why); start with just the convention/header.

   - **`vocab/ledger.csv`** — correct headers: a stable first field (the canonical headword **with its article** for gendered languages, per the ledger dedup convention in `CLAUDE.md`), the target-language fields (per the vocabulary conventions), an **optional IPA column**, an example sentence, and a per-session tag. **`vocab/README.md`** — the Anki import steps.

   - **Directories:** `grammar/` (the cumulative reference library), `lessons/` (per-session folders created by `/lesson`), and `progress/`. Place a `.gitkeep` in each empty scaffolded dir (`lessons/`, `grammar/`, `progress/`).

   - **The folder structure** from §3, and the `.gitignore`. Do **not** create `recaps/`, `writing/`, `exercises/`, or `assessments/` directories. Do **not** scaffold `progress.md` — it is a derived snapshot generated **on demand** by `/progress` (the read-only journey-synthesis skill), never part of the blank scaffold. Do **not** recreate the skills in `.claude/skills/` — they already exist (and there is **no** `/speak` skill).

6. **PHASE 2 — generate `roadmap.md` and `themes.md`.** With the scaffold in place, generate both intent documents. Read the `overview.md` you just wrote, the plan parameters in `CLAUDE.md`, and the broad grammar arc from `overview.md`.

   **`roadmap.md`** — emit a **CEFR-tiered, topic-sequenced** grammar roadmap to `roadmap.md` at the repo root:
   - Lay the topics out as an ordered sequence from the learner's current level up to `TARGET_LEVEL`, grouped by CEFR band (e.g., A1 → A2 → B1 → …), each band listing its grammar topics roughly in the order they should be taught. This is what `/lesson` walks to pick the next still-owed topic.
   - **Size it to `PROGRAM_DURATION` × cadence.** Estimate the number of sessions available (`PROGRAM_DURATION` × `SESSIONS_PER_WEEK`, using the same hours estimate as `overview.md`) and distribute the topics across roughly that many sessions so the pace is realistic; if duration is open-ended, sequence the topics without forcing a per-session count and note that `/recalibrate` sets the pace. Index any pacing notes by **session number**, never by calendar dates.
   - Keep `roadmap.md` as the **grammar intent** (the plan); it stays separate from `grammar.md` (the reality of what has actually been covered). `/recalibrate` later adjusts this pace.

   **`themes.md`** — emit the curated **theme track** to `themes.md` at the repo root. This is the **theme intent**, parallel to `roadmap.md` (the grammar intent), and it drives a **second axis orthogonal to grammar**: the current theme supplies the bulk of each session's vocabulary and the context/topic of reading, writing, and listening, while grammar stays roadmap-sequenced.
   - Lay it out as an **ordered list of the most-frequent everyday-conversation themes**, sequenced by **frequency-of-use AND CEFR level** (e.g., greetings & self → food → shopping → transport & directions → daily routine → work/school → health → plans & appointments → past experiences → opinions → …). The learner does **not** choose these — they are the high-utility defaults that come up most in real conversation.
   - Each entry carries: the **theme name**, a few concrete **scenarios / sub-topics**, a **target CEFR band**, and the **key vocab domains**.
   - **Lightly contextualize to the target-language culture** (e.g., local foods, typical settings) but keep it **mostly universal**.
   - Themes **advance adaptively** — `/close-day` owns advancement (when the theme's vocab and competency are solid), so do **not** assign a fixed session count per theme here. `themes.md` is the intent; `STATE.md`'s current-theme / sessions-in-theme tracks the reality.

7. **Report.** Summarize the parameters used (flagging any defaults) and list what was created (`overview.md`, the scaffold, `roadmap.md`, and `themes.md`). Tell the learner the next step: run `/lesson` to start session 1. You may also mention that `/progress` is available any time for a read-only journey-synthesis report (it writes `progress.md` on demand; not yet meaningful with zero sessions).

## Guardrails

- Do not invent a deadline or a level the learner didn't request; use the defaults and label them as defaults.
- Be honest in the expectations section — reaching C1 across all four skills from zero in a few months is rarely realistic. A truthful target keeps a strong result from being read as failure.
- The three required parameters must be filled. If the learner won't provide one, ask again rather than guessing.
- Do **not** recreate the learning skills in `.claude/skills/`; they already exist. There is **no** `/speak` skill — never reference it.
- After writing `overview.md`, building the scaffold, and generating `roadmap.md` and `themes.md` (PHASE 2), stop — do **not** generate lessons or vocabulary; those come later, via `/lesson`.
- Index everything by **session number** (`N`). Use no calendar dates, days, or weeks as cadence anywhere in the files you create; `SESSIONS_PER_WEEK` is only an hours-estimate input.
