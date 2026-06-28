# Language-Learning Plan — Project Brief (Template)

> **Purpose.** This template, together with the `/new-plan` skill it sits beside, generates a personalized `overview.md` that bootstraps a self-study language-learning repository run by Claude Code.
>
> **Workflow:** (1) run `/new-plan` — it asks for your parameters, writes this template into an `overview.md` at the repo root, **builds the scaffold** (`CLAUDE.md` + the blank living docs + the folder structure), **and generates `roadmap.md` + `themes.md` (PHASE 2)**; (2) run `/lesson` to start learning.
>
> **The learning skills already exist** in `.claude/skills/` and never change per plan — `/new-plan` does not create them. What *is* plan-specific lives in `CLAUDE.md`, which the skills read at the start of every session.
>
> Anything in `{{double braces}}` is a parameter to substitute. Anything in `[square brackets]` is an instruction to whoever fills the template — replace it with real, specialized content, never copy it literally.

---

## Parameters

| Parameter | Required? | Meaning | Default if omitted |
|---|---|---|---|
| `{{TARGET_LANGUAGE}}` | **Required** | The language to learn (e.g., German). | — |
| `{{CONTENT_LANGUAGE}}` | **Required** | The language all *learner-facing* output is written in — explanations, corrections, prompts (e.g., Spanish, English). | — |
| `{{SESSION_LENGTH}}` | **Required** | How long one study session is (e.g., 1.5 h). Each `/lesson` is scoped to this. | — |
| `{{LISTENING_SUPPORT_LANGUAGE}}` | Optional | The support/subtitle language for listening — e.g., the second subtitle track in dual-subtitle Easy Languages clips. | Defaults to `{{CONTENT_LANGUAGE}}` |
| `{{PROGRAM_DURATION}}` | Optional | Total length of the plan (e.g., 6 months). | Open-ended; recalibration sets the pace |
| `{{TARGET_LEVEL}}` | Optional | Desired level, ideally CEFR (e.g., B2). | B2 — but always state the *realistic* target for this language and time |
| `{{SESSIONS_PER_WEEK}}` | Optional | Sessions per week, or the weekly pattern. Used **only** to estimate total hours in this `overview.md` — it is **not** a cadence parameter; nothing in the kit is indexed by week. | [Ask once; otherwise assume a sustainable default and say so] |
| `{{REPO_NAME}}` | Optional | Repository name. | [Suggest one, e.g., target language + level] |

---

## How to use this document

This is the foundational context for the project. Claude Code will not have the conversation in which it was created, so everything it needs is here.

`/new-plan` writes this file, builds the scaffold automatically (see §7) — `CLAUDE.md` and the blank living documents — and then generates `roadmap.md` and `themes.md` (PHASE 2). **The skills are already present and are not recreated, and lessons and vocabulary are not generated yet** — those begin with the first `/lesson`. If anything is ambiguous, ask before assuming.

---

## 1. Objective & learner framing

**Goal:** reach **{{TARGET_LEVEL}} in {{TARGET_LANGUAGE}}** [if `PROGRAM_DURATION` is set, append: "in {{PROGRAM_DURATION}}"], through self-study.

**Learner profile.** [Fill in what's known: native language(s), other languages and their levels, relevant strengths. Prior languages are the strongest predictor of success — a proven multilingual learner learns faster. Name any language the learner already knows that bridges to {{TARGET_LANGUAGE}} through shared vocabulary or structure, since that materially lowers the difficulty.]

**Honest expectations — do not over-promise.** Progress will be **asymmetric**, and the realistic target depends heavily on how far {{TARGET_LANGUAGE}} is from the learner's existing languages. [Specialize: state a realistic landing per skill. Typically reading and writing run ahead; listening at native speed and speaking lag, because those are gated by exposure hours rather than cleverness. If {{TARGET_LEVEL}} is a stretch in the time available, say so plainly here, so a strong result is not read as a failure against an unrealistic number.]

**Time budget.** Each session is **{{SESSION_LENGTH}}**. [If `SESSIONS_PER_WEEK` is set, compute and state the weekly hours; if `PROGRAM_DURATION` is also set, compute and state the approximate total hours. Then compare that total against the guided hours typically needed to reach {{TARGET_LEVEL}} in {{TARGET_LANGUAGE}} for a {{CONTENT_LANGUAGE}} speaker, and say whether the target is comfortable, tight, or a stretch. If those inputs are missing, give a qualitative version instead.]

**The binding constraint is HOURS**, not method or motivation. [If a weekly pattern is given, name the most fragile blocks — e.g., long weekend sessions — and say to protect them like appointments, because that is where the level is actually bought.]

---

## 2. Coach role & teaching principles (these go into `CLAUDE.md`)

You are the learner's {{TARGET_LANGUAGE}} coach, running the day to day. These are the standing rules the skills rely on, so they must all live in `CLAUDE.md`:

- **Plan parameters (the skills read these):** target language = {{TARGET_LANGUAGE}}; content language = {{CONTENT_LANGUAGE}}; session length = {{SESSION_LENGTH}}; target level = {{TARGET_LEVEL}}; duration = {{PROGRAM_DURATION}}. **Everything in the kit is indexed by session number `N`, never by calendar date, day, week, or month.**
- **Language — scaffolding vs. content (global rule):** all *scaffolding* is in **English** (skill files, frontmatter, field names in `STATE.md` / `grammar.md`, template headers). All *learner-facing output* is in **{{CONTENT_LANGUAGE}}** (grammar explanations, corrections, prompts, recaps, conversation). The **target language is {{TARGET_LANGUAGE}}**, which appears as the language being learned. A content *example* inside a SKILL.md is written in {{CONTENT_LANGUAGE}} even though the surrounding instructions are in English — it is content, not syntax.
- **Vocabulary conventions for {{TARGET_LANGUAGE}} (the single source for the ledger):** [Specialize. For gendered languages, always record nouns with their article and plural (e.g., German "das Haus, die Häuser"). For cased languages, note the relevant case behavior. For tonal languages, always mark tone. For verbs, record the forms that are not predictable. State the conventions that matter for {{TARGET_LANGUAGE}} so the learner never has to retrofit them.] **Canonical headword & dedup key (authoritative — both `/lesson` and `/harvest` cite this):** the ledger's stable **first field** is the canonical headword written **with its article** for gendered languages (e.g. "das Haus") — the article is **part of** the canonical form. The **dedup key** is that first field compared **case-insensitively** (lowercased); the article is **never stripped**. `/lesson` and `/harvest` both de-duplicate on exactly this key — there is no other normalization.
- **Pronunciation note for {{TARGET_LANGUAGE}}:** [Specialize. State the per-language pronunciation pitfalls a {{CONTENT_LANGUAGE}} speaker should watch — e.g., German "ch"/umlauts, French nasal vowels, Mandarin tones, Spanish "rr". The `vocab/ledger.csv` carries an optional IPA column for the hard items; there is no separate pronunciation drill skill.]
- **Listening sources for {{TARGET_LANGUAGE}} (`LISTENING_RESOURCES`):** [Specialize, language-agnostic in spirit but concrete here. Name the level-appropriate listening sources `/lesson` draws on to build the every-session `04-listening` segment: the relevant **Easy Languages** series (Easy German, Easy Spanish, Easy French, Easy Italian, etc. — pick the one matching {{TARGET_LANGUAGE}}), plus level-appropriate podcasts and graded-listening resources for {{TARGET_LANGUAGE}}. Prefer transcript/subtitle-bearing sources; dual-subtitle Easy Languages is the default. List them so the skill can pick a clip without re-deciding the catalog each session.]
- **`LISTENING_SUPPORT_LANGUAGE` = {{LISTENING_SUPPORT_LANGUAGE}}** (defaults to {{CONTENT_LANGUAGE}}) — the support/subtitle language `/lesson` pairs with {{TARGET_LANGUAGE}} so dual-subtitle Easy Languages is the default; the learner checks comprehension against the transcript as a self-check.
- **Graded vs. self-reported skills.** The **objectively-graded** segments are **grammar, reading, `00-check`, and writing** (writing holistically via `/grade-writing`) — these produce `/grade` review files and `progress/scores.csv` rows. **Listening and speaking are SELF-REPORTED**: neither is graded by `/grade`, neither produces a `scores.csv` row or a `/grade` review file. The `04-listening` worksheet holds comprehension questions (for the learner's own active-listening self-check), a new-words slot (still flowing to the ledger / `/harvest`), and a "how it felt / self-rated comprehension" field; `/close-day` asks how listening and speaking each felt and logs both, and `/recalibrate` estimates the listening and speaking levels from those self-reports (not from `scores.csv`). `/lesson`'s `scores.csv`-driven adaptive difficulty applies only to the graded segments; listening's allocation/difficulty is driven by `STATE.md`'s per-skill listening level (set by `/recalibrate`).
- **When correcting, explain the *why*, not just the what.** When grading open/fill-in/produced answers, **accept any equivalent correct answer** — synonyms, valid alternative phrasings, acceptable spelling/case/spacing variants — never mark a right answer wrong just because it doesn't match one expected string; still explain genuine errors. MC/TF items grade exactly.
- **Assessment item-format policy (applied by `/lesson` when it builds exercises/tests and by `/grade` when it grades).** **Default to PRODUCTION / fill-in** — cloze, transformation, short open answer, and (sparingly) {{CONTENT_LANGUAGE}}→{{TARGET_LANGUAGE}} translation. Recall beats recognition (the testing effect) and builds productive ability; this kit can afford rich production formats because `/grade` is an LLM — there is **no rigid answer key**, so open/produced answers are gradable. That is the kit's edge over recognition-only apps; lean into it. Use **multiple-choice / true-false / matching deliberately and as a MINORITY**, only where it is genuinely the best tool: (a) **discriminating confusable forms** (e.g. ser/estar, der/die/das, por/para, tense pairs) — when the skill *is* choosing correctly between near-options, MC with those options is ideal and diagnostic; (b) **reading/listening comprehension gist** — MC/TF/matching isolate understanding from production, so you don't conflate "didn't understand" with "couldn't produce"; (c) **early scaffolding / context-completion** — an MC-cloze when full production is still too hard; (d) **fast diagnostic items in the `00-check`**. **MC quality rule:** every MC/TF must have **diagnostic distractors** — each wrong option maps to a specific real misconception; never a lazy MC with one obvious answer. Don't over-rely on translation (it induces translation-thinking); vary production types (cloze, transformation, context/picture-prompted production, answer-a-question). **Format by layer:** `00-check` → fast (short cloze + a couple of diagnostic MC); `02-grammar` → production-biased (cloze, transformation, translation; MC only for confusable contrasts); `03-reading` / `04-listening` → comprehension mix (MC/TF for gist, open short-answer for detail); `03-writing` → open production (holistic, graded by `/grade-writing`); `05-test` at the 7th session (15 min) → balanced mix, production-heavy; `05-test` at the 28th session (90 min) → exam-like, sections per skill, multi-format, mirroring a real proficiency test.
- **Vocabulary cap — a shared per-session TOTAL.** ~15–30 new vocabulary items per session, logged to the ledger — **mostly the current theme's vocab (the bulk)** plus some high-frequency general words (don't narrow exposure to only the theme). The cap is the throttle and is **shared** across `/lesson` introductions and `/harvest` (harvest tops up *toward* the cap, never on top of it); do not overflow it. It flexes down when the learner reports a large Anki review backlog.
- **Front-load the compressible work; expect the rest to take hours.** The systematic, rule-based parts of {{TARGET_LANGUAGE}} compress well for a sharp learner; the exposure-gated parts — vocabulary breadth, listening at native speed, speaking automaticity — do not yield to cleverness. Prioritize input volume and output.
- **At the start of every session, read `STATE.md` first; at the end, update it** (via `/close-day`).
- **Each `/lesson` is one session of advancement (~{{SESSION_LENGTH}})** — lighter on test sessions.
- **Per-session rotation (the load rule).** A fixed **spine runs every session**: `00-check` (the graded retrieval warm-up that opens the session), `01-vocab`, `02-grammar`, and `04-listening`. **Reading and writing SHARE slot `03`**: exactly one of `03-reading` *or* `03-writing` runs per session (never both), **alternating** one full version each session — run whichever did **not** run last (the authoritative rule; cold start: session 1 = reading; parity of `N` is only an illustrative aside). Each may hold **one or more** exercises/tasks (a single one is often too little). **Grammar advances the roadmap every session.** Listening is the **short staple (~10–15 min)**; the heavier academic segments carry the bulk and **trim, never zero**, so every segment's depth scales to fit {{SESSION_LENGTH}}.
- **Themes are a second axis, orthogonal to grammar.** The grammar roadmap (`roadmap.md`) is sequenced by difficulty and a theme **never** reorders it. The **current theme** (from `themes.md`, tracked in `STATE.md`) drives (a) the session's new **vocabulary** (the bulk of it) and (b) the **context/topic** of reading (`03-reading`), writing (`03-writing`), listening (`04-listening`), and live speaking. Grammar rides its own track; the theme rides on top supplying vocab + context.
- **Input vs output (critical):** **INPUT** (`03-reading` + `04-listening`) is on the current theme and **may carry grammar above the current roadmap point** — that is welcome (comprehensible input, i+1): **gloss** such structures briefly ("this is X — covered later; get the gist"), do **not** drill them, and keep the text overall comprehensible. **OUTPUT** (`03-writing` + live speaking) stays **within the grammar taught so far** (roadmap up to now) plus the theme vocab — **never** require the learner to produce a structure not yet taught; a writing task on the theme must be solvable with current grammar.
- **Recalibrate against the learner's real data, not the average.**
- **Speaking is done live throughout the session** — there is no speaking segment and no speaking skill. It is still tracked as a skill level; `/close-day` asks a short speaking self-report so `/recalibrate` has a trace.
- **How to practice & self-assess speaking (no skill grades it, so do it yourself):** **shadow** the Easy Languages listening clips — play a line, then mimic the speaker out loud for rhythm and prosody — and **record yourself and compare against a model**, using references like **Forvo** (native recordings of single words), **YouGlish** (one word across many real clips in context), or **Google Translate TTS** as a quick check. This is the loop that turns input into speaking automaticity.

---

## 3. Repository structure

```
{{REPO_NAME}}/
├── CLAUDE.md              # constitution (§2) + plan parameters + LISTENING_RESOURCES + pronunciation note + "read STATE.md first"
├── overview.md            # this document, personalized — the project's source of truth
├── STATE.md               # the now: current session N, level per skill, focus, ledger pointer, current theme + sessions-in-theme
├── roadmap.md             # the GRAMMAR topic sequence (generated by /new-plan PHASE 2)
├── themes.md              # the THEME track: ordered everyday themes by frequency + CEFR (generated by /new-plan PHASE 2)
├── recap.md               # rolling digest of the LAST 5 SESSIONS (regenerated by /close-day)
├── weak-spots.md          # the churn table: spot | source | category | first/last_seen_session | times_recurred | status
├── LEARNING-PACE.md       # THROUGHPUT only: prescribed vs completed load + per-segment multipliers
├── progress.md            # the journey synthesis snapshot, generated on demand by /progress (read-only)
├── README.md              # (optional) human-facing overview
├── .gitignore             # OS junk, CLAUDE.local.md
│
├── grammar.md             # REGISTER of topics covered, 3 states + the SESSION of each transition (§4)
├── grammar/               # cumulative REFERENCE (the explanations) — <topic>.md
│   └── .gitkeep
│
├── vocab/
│   ├── ledger.csv         # single cumulative vocabulary register (upstream of Anki); optional IPA column
│   └── README.md          # exact Anki import steps
│
├── progress/
│   ├── scores.csv         # append-only: session, segment, skill, items, correct, pct, self_difficulty_1to5, tier
│   ├── level-history.md   # append-only: one row per /recalibrate run (session N, CEFR per skill, what changed & why)
│   └── .gitkeep
│
├── lessons/               # the sessions (generated by /lesson)
│   ├── .gitkeep
│   └── session-NNN/       # everything for ONE session, consolidated
│       ├── lesson.md      #   the session plan/overview (warm-up, coverage, time budget, links)
│       ├── recap.md       #   THIS session's recap (written once by /close-day; session N, no calendar date)
│       └── class/         #   materials & work, in numbered segments by the real flow
│           ├── 00-check/           # EVERY session: the graded retrieval WARM-UP — check.md (cumulative-retrieval probe), answers.md, review.md (/grade)
│           ├── 01-vocab/           # EVERY session: new-words.md (same items appended to vocab/ledger.csv)
│           ├── 02-grammar/         # EVERY session: one folder per topic taught (the backbone)
│           │   └── <topic-slug>/   #   grammar.md (links into grammar/<topic>.md),
│           │                       #   exercise-NN.md, answers-NN.md (learner), review-NN.md (/grade)
│           ├── 03-reading/  OR  03-writing/  # ALTERNATE — exactly ONE per session (never both), one full version each:
│           │                       #   03-reading/: exercise-NN.md (passage + comprehension Qs), answers-NN.md (learner), review-NN.md (/grade) — one or more
│           │                       #   03-writing/: task-NN.md (prompt), submission-NN.md (learner), review-NN.md (/grade-writing) — one or more
│           ├── 04-listening/       # EVERY session, short: task.md, answers.md (self-check Qs + new-words slot + "how it felt") — SELF-REPORTED, NOT graded, no review.md, not in scores.csv
│           └── 05-test/            # ONLY on cadence (every 7th and every 28th session): test.md, answers.md, review.md
│                                   # speaking is NOT a segment — done live throughout the session (tracked only)
│
└── .claude/
    └── skills/            # SHIP PRE-BUILT — do not recreate
        ├── new-plan/      # SKILL.md + overview-template.md (this file)
        ├── lesson/        # SKILL.md
        ├── close-day/     # SKILL.md
        ├── grade/         # SKILL.md
        ├── grade-writing/ # SKILL.md
        ├── recalibrate/   # SKILL.md
        └── harvest/       # SKILL.md (optional)
```

Segments are numbered by the real flow of each session in this fixed order. The **spine** runs every session: `00-check` (the graded retrieval warm-up that opens the session), `01-vocab`, `02-grammar`, `04-listening`. `03-reading` and `03-writing` are two contents of the **same slot `03`** and **alternate** — exactly one per session (never both), one full version each; each may hold **one or more** exercises/tasks (a single one is often too little). The test (`05-test`) appears **only on cadence** (every 7th and every 28th session). **Speaking is not a segment** — the learner does it live throughout the session; it is tracked as a skill level but never generated. `/lesson` decides depth and creates the numbered segments.

---

## 4. Document model

The **living** files (the system's brain; `/lesson`, `/close-day`, and `/recalibrate` read these first, before planning from memory):

- **`STATE.md`** — the snapshot of *now* (overwritten). Sectioned: current session `N`, estimated level per skill (reading / listening / writing / speaking), current focus, a pointer to the ledger batch, and the **current theme** (its name / index into `themes.md`) with a **sessions-in-theme** count. **Weak spots are not here** — they live in `weak-spots.md`. Read by `/lesson`; written by `/close-day` and `/recalibrate`.
- **`roadmap.md`** — the *grammar topic sequence* (the grammar intent; stable). Generated by `/new-plan` (PHASE 2). Read by `/lesson`; pace adjusted by `/recalibrate`.
- **`themes.md`** — the *theme track* (the theme intent; parallel to `roadmap.md`). An ordered list of the most-frequent everyday-conversation themes, sequenced by **frequency-of-use AND CEFR level** (e.g. greetings & self → food → shopping → transport & directions → daily routine → work/school → health → plans & appointments → past experiences → opinions → …). The learner does **not** choose them — they are the high-utility defaults. Each entry carries the theme name, a few concrete scenarios/sub-topics, a target CEFR band, and key vocab domains. A theme drives the session's vocab + the context of reading/writing/listening/speaking; it **never** reorders grammar. Generated by `/new-plan` (PHASE 2), lightly contextualized to the target-language culture but mostly universal. Read by `/lesson`; the current theme is **advanced adaptively** by `/close-day`.
- **`grammar.md`** — the *register* of which topics are covered and their state: **introduced / practicing / mastered**, each transition stamped with **the session number it happened** (e.g. `introduced@N`, `practicing@N`, `mastered@N`). Not a binary checkbox: a topic "seen" but still error-prone must be recycled. The transition sessions are load-bearing — `/lesson` uses the least-recently-touched non-active topic for a spaced grammar recycle probe. Read by `/lesson`; written by `/close-day`.
- **`weak-spots.md`** — a single small table tracking churn, session-indexed: `spot | source | category | first_seen_session | last_seen_session | times_recurred | status (active/watch/cleared) | cleared_session`. **`category` is the error TYPE** (e.g. agreement, gender, case, word-order, tense/aspect, preposition, false-friend, spelling, word-choice, register — short tag, the set that fits {{TARGET_LANGUAGE}}), so errors are queryable per-type over time (sets up a future per-category rollup). `/close-day` assigns the category when it adds a new spot (inferred from the `/grade` error pattern) and may refine it on churn. A spot clears only after ≥2 spaced correct reappearances (active → watch → cleared); a re-failure flips it back to active and increments `times_recurred`. Read by `/lesson` (the `00-check` retrieval warm-up is ordered most-churned first); maintained by `/close-day`.
- **`LEARNING-PACE.md`** — **throughput only**: per-segment prescribed vs completed load, self-reported time/difficulty, and one per-segment load multiplier. It carries **no** CEFR / level / roadmap opinion (that is `/recalibrate`'s job). Regenerated by `/close-day` on session 1 and every 3rd session thereafter. Read by `/lesson` (adaptive difficulty) and `/recalibrate`.
- **`vocab/ledger.csv`** — the single vocabulary register (upstream of Anki), with an optional IPA column. Read/written by `/lesson` (and `/harvest` if enabled).

**Append-only progress logs** (under `progress/`):

- **`progress/scores.csv`** — one row per graded segment: `session, segment, skill, items, correct, pct, self_difficulty_1to5, tier`. Written by `/grade` and `/grade-writing`; read by `/lesson` for adaptive difficulty (the trailing ~5 rows per skill).
- **`progress/level-history.md`** — one row per `/recalibrate` run: `session N`, CEFR per skill, and what changed and why.

**`progress.md`** (repo root) is **not** a living document — it is a **DERIVED, overwritten human-facing synthesis** snapshot generated on demand by `/progress` (read-only). Distinct from `progress/level-history.md` (the raw, append-only CEFR log written by `/recalibrate`) and from `LEARNING-PACE.md` (tactical per-session throughput consumed by `/lesson`): `progress.md` reads across all of those and the recaps to give the learner a step-back view of the whole journey, and changes none of them. It is regenerated each `/progress` run and is not part of the blank scaffold.

`roadmap.md` (grammar intent) and `grammar.md` (reality) are **not** merged. `/lesson` reads both — one to know what's next, the other to know what's still owed. `themes.md` (theme intent) is the **second, orthogonal axis**: `/lesson` reads the current theme from `STATE.md` to source vocab + the reading/writing/listening/speaking context, while grammar advances independently along `roadmap.md`.

**Recaps.** The **root `recap.md`** is a rolling digest of the **last 5 sessions** — regenerated every session by `/close-day` (newest in, 6th-oldest dropped); this is what `/lesson` reads for recent context. Each session also keeps its own **`lessons/session-NNN/recap.md`**, written once by `/close-day` (frontmatter: session `N` + actual duration + scores; **no calendar date**), the permanent per-session record. Both are distinct from `STATE.md`, which is overwritten while the per-session recaps accumulate in git history.

**Reference** (grows; the study material): `grammar/<topic>.md` (the cumulative explanations, linked from each session's grammar segment), `vocab/README.md`. **Work & material:** everything under `lessons/session-NNN/` — `lesson.md` (the plan, **always written**, even on a test-only session) and `class/` with its numbered segments, in this fixed order: `00-check` (the graded retrieval warm-up), `01-vocab`, `02-grammar/<topic-slug>`, then `03-reading` **or** `03-writing` (exactly one per session, alternating, with one or more exercises/tasks), `04-listening` (every session), `05-test` (cadence only) — the actual check/vocab/grammar/reading-or-writing/listening/test work for that session. Speaking is not a segment (done live, tracked only).

---

## 5. Skills (index)

The full, authoritative spec for each skill is its own `.claude/skills/<name>/SKILL.md`. They ship pre-built and are plan-agnostic — they read every plan-specific value (content language, target language, session length, vocabulary conventions, listening resources) from `CLAUDE.md`. Summary:

- **`/new-plan`** — this skill: collect parameters, write `overview.md`, build the scaffold (§7), and **generate `roadmap.md` and `themes.md` (PHASE 2)** — the session-sequenced grammar plan and the frequency-and-CEFR-ordered theme track. Run once at the start of a fresh repo.
- **`/lesson`** — create one study session (~{{SESSION_LENGTH}}) under `lessons/session-NNN/`, informed by the root `recap.md` (last-5-session digest). **Adaptive:** it reads the trailing ~5 rows per skill from `progress/scores.csv` plus the `LEARNING-PACE.md` multipliers — 3 consecutive ≥90% on a segment bumps that segment's level; any <70% eases it. It **always writes `lesson.md`** (the plan/overview, opening with a short "why today" tied to the weak spots, the **current theme** (the situation you're building toward, from `STATE.md` / `themes.md`), and the new grammar topic, plus a one-line "last time" recall) and builds the numbered `class/` segments, scaling each to fit {{SESSION_LENGTH}}. **Spine every session:** the session **opens with the graded retrieval warm-up `00-check/`** — a ~5–10 min cumulative-retrieval probe built from `weak-spots.md` (ordered most-churned first) plus a spaced grammar-recycle probe (the least-recently-touched non-active topic) and escalation (a re-failed previously-cleared item gets an extra `02-grammar/<topic>/` folder that session, with its normal exercise/answers/review trio); it is a retrieval of *prior* material + active weak spots, never today's new topic — then ~15–30 new vocab items in `01-vocab/new-words.md` (mostly the **current theme's** vocab plus some high-frequency general words; also appended to `vocab/ledger.csv`; the cap is a total shared with `/harvest`), the next grammar topic(s) in `02-grammar/<topic-slug>/` (with `exercise-NN.md`; grammar advances along `roadmap.md` **independent of the theme**), and a short `04-listening/` (~10–15 min on the **current theme**, pointing at the `LISTENING_RESOURCES` from `CLAUDE.md`, dual-subtitle in {{LISTENING_SUPPORT_LANGUAGE}}; offline fallback emits a generic gist+detail + dictation micro-task). **Listening is INPUT** — it may carry grammar above the current roadmap point: gloss such structures briefly, don't drill them, keep the clip overall comprehensible. **Rotating main course in slot `03`:** `03-reading/` and `03-writing/` alternate — exactly one per session (never both; run whichever did **not** run last; session 1 starts with reading; a test-only 28th session doesn't consume the slot), each holding **one or more** exercises/tasks (a single one is often too little: `exercise-NN.md` for reading, `task-NN.md` for writing); both are set in the **current theme** and reuse active weak-spot grammar and the last 1–2 sessions' vocab. **Reading is INPUT** — it may carry grammar above the current roadmap point (gloss briefly, don't drill, keep it comprehensible). **Writing is OUTPUT** — it stays **within the grammar taught so far** plus the theme vocab; the task must be solvable with current grammar (never require an untaught structure). The writing task is framed as a **concrete CASE / SCENARIO within the current theme** — a real situation the learner responds to in writing (e.g. theme = restaurant → "write a short message complaining that a dish arrived cold and asking for a fix"), varied across sessions. The reading material and the writing task each **vary between a conversation/dialogue and a continuous prose text** — rotate across sessions for register variety (spoken-style dialogue vs written prose), with the scenario framing on top of that register variety. **Assessments are production-biased** (cloze, transformation, short open answer; MC/TF used deliberately as a minority per the §2 item-format policy, with diagnostic distractors). **`/lesson` generates the answer files as fillable worksheets**, not just declaring where the learner writes: alongside each task/prompt file it creates a ready-to-fill companion that reproduces the items/questions with blank answer slots, so the learner just fills them in (no creating files or guessing paths) — `00-check/answers.md`, `02-grammar/<topic>/answers-NN.md` (one per `exercise-NN.md`), `03-reading/answers-NN.md` (one per reading `exercise-NN.md`), `03-writing/submission-NN.md` (the prompt plus a blank area to write; one per `task-NN.md`), `04-listening/answers.md` (self-check questions with blanks, a "new words" slot, and a "how it felt / self-rated comprehension" field — self-reported, not graded), and `05-test/answers.md` on a test session. The task/prompt files (`check.md`, grammar `exercise-NN.md`, reading `exercise-NN.md`, writing `task-NN.md`, listening `task.md`, test `test.md`) stay as the prompts; `/grade` and `/grade-writing` read the filled worksheet. `/lesson` does **not** build a speaking segment — speaking is done live throughout the session. A `05-test/` appears **only on cadence**: a 15-minute consolidation test every **7th** session, and a **standalone 90-minute (1h30) test every 28th** (test only, no new teaching, runs longer than a normal session). Never combine a full lesson and a large test in one session; on the 28th-session test day, `lesson.md` states it is the 90-minute assessment (what it covers, no new material) and the only segment is `05-test/`. On session 1 (cold start), `lesson.md` also carries the first-run orientation (the loop in 4 steps) and `00-check` becomes a short level-placement diagnostic.
- **`/grade`** — grade a test or objective exercise set passed as an argument (no-arg fallback: the most-recent ungraded answers); grades the **objectively-graded** segments only (`00-check`, `02-grammar`, `03-reading`, and tests) — **not `04-listening`, which is self-reported**; corrections with the *why* plus a recurring-error summary, saved as `review-NN.md` (or `review.md`) next to the matching `answers` file, **and a row appended to `progress/scores.csv`**. One skill for all test sizes.
- **`/grade-writing`** — holistic writing correction with explanations, register notes, and a fully corrected version. Reads `03-writing/submission-NN.md` and writes `review-NN.md` (or `submission.md`/`review.md`) next to it, **and a row appended to `progress/scores.csv`**. Explicit.
- **`/close-day`** — read this session's `review-NN.md` / `review.md` files (`/grade` and `/grade-writing` output, including `00-check/review.md`; listening has no review file — it is self-reported) plus the self-report; **maintain `weak-spots.md`** (fold the `00-check` retrieval result into the churn: flip active→watch→cleared only after ≥2 spaced correct reappearances, re-fail flips back to active); write `lessons/session-NNN/recap.md` and **regenerate the root `recap.md`** as the rolling last-5-session digest; record the **grammar transition sessions** in `grammar.md`; **regenerate `LEARNING-PACE.md`** (session 1 and every 3rd session); advance the session counter idempotently; **advance the theme adaptively** — move to the next theme in `themes.md` when the current theme's vocab scores are solid in `progress/scores.csv`, it stops generating new weak spots, and the learner handles its reading/writing without major errors (**guardrails:** stay in a theme **at least ~3** sessions, **at most ~10** — force-advance so it never drags), updating `STATE.md`'s current-theme and sessions-in-theme; **celebrate** cleared weak spots (with the session span) and newly-mastered topics in both the report and the recap; ask a **listening + speaking self-report** ("how did listening feel / did you speak today and how did it feel") logged into the recap (both are self-reported skills); refresh `STATE.md`; commit. When the just-closed session `N` is a multiple of 28, it **reminds the learner to run `/recalibrate` next** (the reminder is the only automatic trigger; `/recalibrate` stays manual).
- **`/recalibrate`** — every **28th** session: read the `scores.csv` curve + `weak-spots.md` + recaps + the 90-minute test at `lessons/session-*/class/05-test/review.md`, re-estimate CEFR level per skill — the graded skills (reading / writing / grammar) from `scores.csv`, and the **listening and speaking levels from the `/close-day` self-reports in the recaps** (those skills have no `scores.csv` rows) — adjust the `roadmap.md` pace, update `STATE.md`, and **append a row to `progress/level-history.md`**. Estimates from recaps if no test exists yet. **Bonus (optional, light):** if an advanced structure **recurs in the input** across sessions, it MAY flag that structure as a candidate to **pull forward** in `roadmap.md` (the input signals which pulls are worth it). Explicit and **manual** (never auto-invoked; `/close-day` only reminds after a 28th session).
- **`/progress`** — a **read-only, on-demand journey synthesis** for the learner (human-facing, in the content language). Reads `progress/scores.csv`, `progress/level-history.md`, `weak-spots.md`, the recent `lessons/session-*/recap.md` (incl. the **listening + speaking self-reports**), `STATE.md`, `roadmap.md` + `themes.md`, and `CLAUDE.md`, then produces a step-back view nothing else surfaces between recalibrations: **per-skill trend & current level** (reading/grammar/writing from the `scores.csv` slope + level-history; listening & speaking qualitatively from the recap self-reports — note the asymmetry), **plateau detection** (any skill flat or declining over roughly the last several sessions), **top recurring error categories** (aggregated from the `weak-spots.md` category column, active-vs-cleared and trending-down or sticky), **on-track vs plan** (sessions done vs roadmap/themes progress against the target level/duration — ahead / on-track / behind, honestly), **wins / milestones** (cleared weak spots with their session span, newly-mastered grammar, themes completed, current vocab/ledger count), and **one actionable suggestion per plateau or sticky error** (advice only). It **writes ONLY `progress.md`** at the repo root (its own overwritten snapshot) and **changes no living document** (`STATE.md`, `weak-spots.md`, `scores.csv`, `level-history.md`, `roadmap.md`, `themes.md`, `grammar.md`, `LEARNING-PACE.md`, recaps — all untouched). **Distinct from `/recalibrate`**, which ACTS (re-estimates CEFR and edits `roadmap.md` pace every 28th session) — `/progress` only SHOWS, never auto-invoked, never part of the daily loop. Explicit.
- **`/harvest`** *(optional)* — append the learner's unknown words from a reading to the ledger, correctly formatted, **topping up toward the shared per-session vocab cap (never on top of it)**. Can be folded into `/close-day`.

---

## 6. Key decisions & rationale

- **Use real Anki; do not rebuild spaced repetition.** The ledger is upstream, Anki downstream, one-directional. Anki de-duplicates by the **first field**, which is the canonical headword-with-article defined in §2 (compared case-insensitively, article never stripped) — both `/lesson` and `/harvest` use that same key, so the CSV is already deduped before import. Scheduling/progress lives **inside Anki, not the CSV**, so re-importing only adds new items and never erases progress. Keep new cards/day ≈ the per-session batch; tag each batch by session; save the CSV as **UTF-8**.
- **Do not fragment skills.** Consolidate when the only difference is a parameter (one `/grade` for all test sizes). A skill earns its place with a **repeatable workflow + file effects**; "explain topic X" is just talking to Claude.
- **Plan-specifics live in `CLAUDE.md`, logic lives in the skills.** That separation is what lets the skills be invariant and ship pre-built.
- **Hours are the binding constraint.** Test sessions don't also carry a full lesson.
- **Everything is indexed by session number `N`** — no calendar dates, days, weeks, or months as cadence anywhere. (`SESSIONS_PER_WEEK` survives only as an optional hours-estimate input in this `overview.md`.)
- **Weak-spot drilling lives in the graded `00-check` retrieval warm-up** that opens every session and is tracked in `weak-spots.md`, not a separate skill.
- **Speaking is done live, not generated** — there is no `/speak` skill; speaking is still tracked as a skill level via the `/close-day` self-report.
- **Keep the skill set small** so descriptions aren't trimmed from context.

---

## 7. Scaffold (built automatically by `/new-plan`)

After writing this file, `/new-plan` builds the rest, then generates `roadmap.md` and `themes.md` (PHASE 2). The skills already exist under `.claude/skills/` and are **not** recreated. What gets created:

1. **`CLAUDE.md`** — containing the §2 teaching principles, the **plan parameters** (target language, content language, session length, target level, duration — but **not** `SESSIONS_PER_WEEK`, which is only an optional hours-estimate input here, not a standing parameter), the {{TARGET_LANGUAGE}} **vocabulary conventions**, the {{TARGET_LANGUAGE}} **pronunciation note**, the specialized {{TARGET_LANGUAGE}} **listening sources** (`LISTENING_RESOURCES` — the Easy Languages series plus level-appropriate podcasts / graded listening, so `/lesson` can build the every-session `04-listening` segment), the **`LISTENING_SUPPORT_LANGUAGE`** (= {{LISTENING_SUPPORT_LANGUAGE}}, default {{CONTENT_LANGUAGE}}), and "read `STATE.md` first." The pre-built skills read these values from `CLAUDE.md`, so they must be present and accurate.
2. **Blank living docs:**
   - `STATE.md` — sectioned (current session `N`, level per skill, focus, ledger pointer, current theme + sessions-in-theme), no progress data; weak spots live elsewhere.
   - `grammar.md` — empty, with the three-state convention plus the transition-session stamp format.
   - root `recap.md` — empty placeholder (the rolling last-5-session digest, filled in by `/close-day`).
   - `weak-spots.md` — empty, with the churn-table header (`spot | source | category | first_seen_session | last_seen_session | times_recurred | status | cleared_session`), where `category` is the error type for per-type tracking.
   - `LEARNING-PACE.md` — empty placeholder (throughput-only; regenerated by `/close-day` on session 1 and every 3rd session).
   - `progress/scores.csv` — header row only (`session, segment, skill, items, correct, pct, self_difficulty_1to5, tier`).
   - `progress/level-history.md` — empty placeholder (appended by `/recalibrate`).
   - `vocab/ledger.csv` — correct headers (a stable first field, the {{TARGET_LANGUAGE}}-appropriate fields, an optional IPA column, an example sentence, a per-session tag).
   - `vocab/README.md` — the Anki import steps.
3. **The folder structure** from §3 (`grammar/`, `vocab/`, `progress/`, `lessons/` — no `recaps/`, `writing/`, `exercises/`, or `assessments/`), with **`.gitkeep`** in the empty scaffolded dirs (`grammar/`, `progress/`, `lessons/`), and the `.gitignore`.
4. Do **not** recreate the skills in `.claude/skills/` — they already exist (and there is **no** `/speak` skill).
5. **Then generate `roadmap.md` and `themes.md` (PHASE 2)** — `roadmap.md` is the CEFR-tiered, session-sequenced **grammar** plan; `themes.md` is the **theme track**, an ordered list of high-utility everyday-conversation themes sequenced by frequency + CEFR (each entry: theme name, concrete scenarios/sub-topics, target CEFR band, key vocab domains), lightly contextualized to {{TARGET_LANGUAGE}} culture but mostly universal. Do **not** generate lessons or vocabulary yet.
6. If anything is ambiguous, **ask before assuming**.

When the scaffold, `roadmap.md`, and `themes.md` are done, report what was created.
