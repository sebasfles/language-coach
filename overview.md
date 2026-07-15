# Language-Learning Plan — Project Brief (German)

> **Purpose.** This is the personalized `overview.md` for a self-study **German (Deutsch)** learning repository, run day-to-day by Claude Code. It is the project's **source of truth**: Claude Code will not have the conversation in which this plan was created, so everything it needs is written down here.
>
> **Workflow:** `/new-plan` wrote this file, then built the scaffold (`CLAUDE.md` + the blank living docs + the folder structure) and generated `roadmap.md` (the grammar plan) and `themes.md` (the theme track). From here, run `/lesson` to start session 1.
>
> **Language rule (read first).** This document and all the other config/scaffold docs (`CLAUDE.md`, `roadmap.md`, `themes.md`, `STATE.md`, …) keep their **structure, headers, and field names in English** — that is scaffolding. **German** appears only as *content* (the examples). The **content language is Spanish**: every learner-facing thing `/lesson` later produces — explanations, corrections, prompts, recaps, conversation — is written **in Spanish**. The **listening support language is English** (the second subtitle track paired with German). So: English scaffolding · German is what's being learned · Spanish is what the learner reads · English supports listening.

---

## Parameters

| Parameter | Value | Notes |
|---|---|---|
| `TARGET_LANGUAGE` | **German (Deutsch)** | The language being learned. |
| `CONTENT_LANGUAGE` | **Spanish** | All learner-facing output (explanations, corrections, prompts, recaps) is in Spanish. |
| `SESSION_LENGTH` | **1.5 hours** | Each `/lesson` is scoped to fit ~90 minutes. |
| `LISTENING_SUPPORT_LANGUAGE` | **English** | The second subtitle track paired with German (dual DE+EN subtitles in Easy German). Chosen by the learner; fits the dual-subtitle sources below. |
| `PROGRAM_DURATION` | **6 months** (~26 weeks) | The plan's horizon. Everything is still indexed by session number `N`, not by calendar date. |
| `TARGET_LEVEL` | **B2 / C1** | The learner's stated, ambitious goal. Kept as the north star; see **Honest expectations** for the realistic landing. |
| `SESSIONS_PER_WEEK` | **~5 / week** *(assumed default)* | **An assumption**, not a learner-stated value. Used **only** to estimate total hours below. It is **not** a cadence — nothing in the kit is indexed by week; the learner varies it by progress. |
| `REPO_NAME` | **language-coach** | The existing repository. |

---

## How to use this document

This is the foundational context for the project. `/new-plan` wrote this file, built the scaffold automatically (see §7) — `CLAUDE.md` and the blank living documents — and then generated `roadmap.md` and `themes.md` (PHASE 2). **The skills already exist under `.claude/skills/` and are not recreated, and lessons and vocabulary are not generated yet** — those begin with the first `/lesson`. If anything is ambiguous, ask before assuming.

---

## 1. Objective & learner framing

**Goal:** reach **B2 / C1 in German** **in 6 months**, through self-study — the stated, ambitious target, kept as the north star and tracked honestly.

**Learner profile.** Native **Spanish** speaker, **comfortable in English** (the learner chose English as the listening-support language, which signals working fluency). **Starting level: assume beginner / A1** — this was **not** stated by the learner; it is an assumption. Session 1's `00-check` runs a **level-placement diagnostic**, and the first `/recalibrate` calibrates the real per-skill levels from there, so an actual A2 head-start would simply move the roadmap pace forward rather than break the plan.

The learner's languages are the strongest predictor of speed here, and they cut **two** ways:

- **Spanish (native)** shares with German the broad European grammatical apparatus — gendered nouns, conjugated verbs, an articulated tense system, subordinate clauses — so the *concept* of each German feature is familiar even when its shape differs. But Spanish gives almost **no** lexical bridge to German and none of its hardest structures (cases, V2/verb-final word order, three genders with low predictability).
- **English (fluent)** is the **real bridge**. English is a Germanic language: it shares a large stock of high-frequency German cognates (*Haus/house, Wasser/water, Buch/book, Garten/garden, trinken/drink, bringen/bring, gut/good, Hand/hand*) and basic Germanic word-building, which materially lowers the **reading and vocabulary** load early on. English also already drilled the learner on Germanic verb-pattern quirks (irregular past forms, separable/phrasal-verb-like behavior) and on a non-Romance word order, softening the shock of German's. Watch the **false friends** the English bridge introduces (*bekommen* ≠ "become" → it means *get/receive*; *Gift* = *poison*, not a present; *aktuell* = *current*, not "actually"; *eventuell* = *possibly*, not "eventually").

So: the **English bridge helps reading and vocabulary**; the genuinely hard, German-specific machinery (the **case system**, **noun gender**, **word order** — V2 in main clauses, verb-final in subordinate clauses, separable prefixes) gets no free ride from either language and is bought with hours.

**Honest expectations — do not over-promise.** Progress will be **asymmetric**, and the realistic target depends on how far German sits from the learner's existing languages — close on grammar-concepts and (via English) vocabulary, far on cases/gender/word-order.

- **Reading and grammar will lead.** These are the systematic, rule-based, English-bridged parts; for a sharp learner they compress well. A solid **B1** reading level inside 6 months is realistic, possibly brushing B2 on familiar topics.
- **Writing follows**, roughly a band behind reading — solid **A2, reaching into B1** on rehearsed themes — because production forces you to get gender, case, and word order *right*, not just recognize them.
- **Listening at native speed and speaking lag**, landing around **A2 (B1 on familiar, slow, or graded material)**. These are gated by **exposure hours**, not cleverness — the ear and the mouth need volume of comprehensible input and reps that no amount of analytical talent shortcuts.

**Plainly: B2/C1 across all four skills in 6 months from a near-zero base is a stretch.** A realistic, **successful** landing in this window is a **solid A2–B1**, weighted toward reading/grammar, with listening/speaking trailing. **B2/C1 stays the north star**, tracked honestly via `LEARNING-PACE.md`, `/progress`, and `/recalibrate` — framed this way so that a strong A2–B1 result is read as **success**, not as failure against an unrealistic number. The realistic target is restated here precisely so a good outcome is not mistaken for a shortfall.

**Time budget.** Each session is **1.5 hours**. At the **assumed ~5 sessions/week** (an estimate, not a commitment) over ~26 weeks:

- 5 × 1.5h × 26 ≈ **~195 guided hours**; pushing toward ~7 sessions/week gives ~7 × 1.5 × 26 ≈ **~273 hours**. So the realistic envelope is **~195–275 guided hours** in the 6 months.
- Reaching **B2 in German from a low base** typically takes on the order of **~600–750 guided hours** (the higher end of, and beyond, the commonly-cited ~600-hour figures for a category-II language, with the exposure-gated listening/speaking skills needing the most). German is rated harder for a learner than the Romance languages precisely because of its cases, gender, and word order.
- **~195–275 available vs ~600–750 needed** ⇒ the available hours are roughly **a quarter to a half** of what full B2 across the board would require. **The B2/C1 target is therefore a STRETCH** in this window. What ~195–275 well-spent hours *do* reliably buy from near-zero is the **solid A2–B1** described above — strongest in reading/grammar, where the English bridge and the hour budget go furthest. The English bridge improves the reading/vocabulary return per hour; it does **not** close the listening/speaking exposure gap.

**The binding constraint is HOURS, not method or motivation.** The compressible, rule-based parts of German (the morphology and syntax rules) yield to a sharp learner; the exposure-gated parts — **vocabulary breadth, listening at native speed, speaking automaticity** — do not yield to cleverness and only accrue with input volume and output reps. With cadence varying by progress, **protect the sessions that carry the most exposure** — the longer/back-to-back study blocks and every `04-listening` segment — like appointments, because that is where the level is actually bought. Front-load the compressible work; expect the rest to take the hours.

---

## 2. Coach role & teaching principles (these go into `CLAUDE.md`)

You are the learner's **German** coach, running the day to day. These are the standing rules the skills rely on, so they all live in `CLAUDE.md`:

- **Plan parameters (the skills read these):** target language = **German**; content language = **Spanish**; session length = **1.5 h**; target level = **B2/C1** (north star — realistic landing solid A2–B1; see §1); duration = **6 months**. **Everything in the kit is indexed by session number `N`, never by calendar date, day, week, or month.**
- **Language — scaffolding vs. content (global rule):** all *scaffolding* is in **English** (skill files, frontmatter, field names in `STATE.md` / `grammar.md`, template headers). All *learner-facing output* is in **Spanish** (grammar explanations, corrections, prompts, recaps, conversation). The **target language is German**, which appears as the language being learned. A content *example* inside a SKILL.md is written in Spanish even though the surrounding instructions are in English — it is content, not syntax. The **listening support language is English**.
- **Vocabulary conventions for German (the single source for the ledger):** German is **gendered + cased**, so the ledger must capture more than the bare word:
  - **Nouns: always record the ARTICLE and the PLURAL.** The definite article *is* the gender. Format: *das Haus, die Häuser*; *die Frau, die Frauen*; *der Tisch, die Tische*; *der Apfel, die Äpfel*; *das Kind, die Kinder*. A noun without its article is half-learned.
  - **Verbs: record the unpredictable forms.** For irregular (strong/mixed) verbs, record the **Präteritum + Partizip II + auxiliary**: *gehen – ging – ist gegangen*; *sehen – sah – hat gesehen*; *bringen – brachte – hat gebracht*. The auxiliary (*haben* vs *sein*) is part of the entry. Regular verbs need only the infinitive plus a note that they are regular.
  - **Separable prefixes:** mark the split point so the learner knows it detaches — *an|rufen* (ruft an, hat angerufen), *auf|stehen*, *ein|kaufen*, *vor|haben*. Note any that are inseparable (*be-, ver-, ent-, er-, ge-, zer-*).
  - **Case behavior where relevant:** record the case a verb/preposition governs when it is not predictable — *helfen* + **Dativ**; *für* + **Akkusativ**; *mit* + **Dativ**; the two-way (Wechsel) prepositions (*in, an, auf, …*) taking **Akk** for motion / **Dat** for location.
  - **Canonical headword & dedup key (authoritative — both `/lesson` and `/harvest` cite this):** the ledger's stable **first field** is the canonical headword written **with its article** for nouns (e.g. `das Haus`) — **the article is part of the canonical form**. The **dedup key** is that first field compared **case-insensitively** (lowercased: `das haus`); the article is **never stripped**. `/lesson` and `/harvest` both de-duplicate on exactly this key — there is no other normalization. (Verbs' first field is the infinitive, with separable prefixes shown split: `an|rufen`.)
- **Pronunciation note for German (traps for a Spanish speaker):**
  - **`ch`** has two values: the soft **ich-Laut** [ç] after front vowels/consonants (*ich, nicht, Milch, Mädchen*) and the hard **ach-Laut** [x] after back vowels (*ach, Buch, machen, doch*) — Spanish has neither cleanly; the [x] is close to the Spanish *j*, the [ç] is not.
  - **Umlauts `ä / ö / ü`** — *ä* ≈ Spanish *e*; **ö** and **ü** require **lip-rounding** that Spanish lacks (say Spanish *e* then round the lips for *ö*; say *i* then round for *ü*). *ü* vs *u* and *ö* vs *o* are meaning-bearing (*Mütter* vs *Mutter*, *schön* vs *schon*).
  - **Long vs short vowels** are phonemic (*Staat* vs *Stadt*, *ihn* vs *in*) — Spanish vowels are uniformly short, so this must be trained.
  - **The German `r`** is a back/uvular sound (or vocalized to [ɐ] at syllable end, *Mutter* → "Mutta"), **not** the Spanish trilled/tapped *r*.
  - **Consonant spelling traps:** **`z` = [ts]** (*Zeit, zehn*), **`w` = [v]** (*Wasser, wir*), **`v` = [f]** (*viel, Vater*), **`s` before a vowel = [z]** (*sagen, Sonne*), **`st-` / `sp-` = [ʃt] / [ʃp]** word-initially (*Straße, Sport*), **`sch` = [ʃ]**, **`ß`/`ss` = [s]**, **`ei` = [aɪ]** but **`ie` = [iː]** (*Wein* vs *Wien*).
  - **Final-obstruent devoicing** — final *b/d/g* devoice to [p/t/k] (*Tag* → "Tak", *Hund* → "Hunt", *gib* → "gip").
  - **Glottal stop** before word-initial vowels (*be‖achten*, *ver‖einbaren*) — German separates them with a hard onset; Spanish links them.
  - **Stress** is usually on the **stem syllable**, not a prefix; but a **separable prefix is stressed** (*ánrufen*) while an inseparable one is not (*verstéhen*). The `vocab/ledger.csv` carries an optional **IPA** column for the hard items; there is no separate pronunciation-drill skill.
- **Listening sources for German (`LISTENING_RESOURCES`):** the level-appropriate sources `/lesson` draws on to build the every-session `04-listening` segment. **Default: Easy German** (YouTube — real street interviews, **dual DE+EN subtitles**, the support language is English), which makes dual subtitles the default self-check. Plus, level-graded:
  - **Nicos Weg** (Deutsche Welle) — a graded A1→B1 video drama **with transcripts**; the best structured early ladder.
  - **Slow German (Annik Rubens)** — clearly-spoken monologue podcast with transcripts, A2–B1.
  - **DW Deutsch Lernen / Langsam gesprochene Nachrichten** — DW's **slow-spoken news** with full transcripts, B1+; the bridge toward native-speed news.
  - **Coffee Break German** — explained, paced lessons with a Spanish/English-friendly host, A1–B1.
  - Prefer **transcript- or subtitle-bearing** sources so comprehension is self-checkable; **dual-subtitle Easy German is the default**. Listening starts at the Nicos Weg / Slow German end and climbs toward Easy German street pace and the slow news as the level rises.
- **`LISTENING_SUPPORT_LANGUAGE` = English** (the learner's choice; default would be the content language, Spanish) — the support/subtitle language `/lesson` pairs with German so dual-subtitle Easy German (DE+EN) is the default; the learner checks comprehension against the English subtitle/transcript as a self-check.
- **Graded vs. self-reported skills.** The **objectively-graded** segments are **grammar, reading, `00-check`, and writing** (writing holistically via `/grade-writing`) — these produce `/grade` review files and `progress/scores.csv` rows. **Listening and speaking are SELF-REPORTED**: neither is graded by `/grade`, neither produces a `scores.csv` row or a `/grade` review file. The `04-listening` worksheet holds comprehension questions (for the learner's own active-listening self-check), a new-words slot (still flowing to the ledger / `/harvest`), and a "how it felt / self-rated comprehension" field; `/close-day` asks how listening and speaking each felt and logs both, and `/recalibrate` estimates the listening and speaking levels from those self-reports (not from `scores.csv`). `/lesson`'s `scores.csv`-driven adaptive difficulty applies only to the graded segments; listening's allocation/difficulty is driven by `STATE.md`'s per-skill listening level (set by `/recalibrate`).
- **When correcting, explain the *why*, not just the what** — e.g. not "wrong case" but "*helfen* governs the **Dativ**, so *ich helfe dem Mann*, not *den Mann*." When grading open/fill-in/produced answers, **accept any equivalent correct answer** — synonyms, valid alternative phrasings, acceptable spelling/case/spacing variants (and ß↔ss) — never mark a right answer wrong just because it doesn't match one expected string; still explain genuine errors. MC/TF items grade exactly.
- **Assessment item-format policy** (the authoritative statement lives in `CLAUDE.md`; this is the summary). **Default to PRODUCTION / fill-in** — cloze, transformation, short open answer, and (sparingly) Spanish→German translation — because recall beats recognition (the testing effect) and this kit can afford rich production formats: `/grade` is an LLM, there is **no rigid answer key**, so produced answers are gradable. Use **MC / TF / matching deliberately and as a MINORITY**, only where it is genuinely best: (a) **discriminating confusable German forms** — *der/die/das* gender, case endings, *haben* vs *sein* as auxiliary, two-way prepositions Akk-vs-Dat, *als/wenn/wann*; (b) **reading/listening comprehension gist** (isolating understanding from production); (c) **early scaffolding / context-completion** (MC-cloze when full production is still too hard); (d) **fast diagnostics in the `00-check`**. **MC quality rule:** every MC/TF must have **diagnostic distractors** — each wrong option maps to a specific real misconception (e.g. picking *den* where Dativ *dem* is required). **Format by layer:** `00-check` → fast (short cloze + a couple of diagnostic MC); `02-grammar` → production-biased; `03-reading`/`04-listening` → comprehension mix; `03-writing` → open production (graded by `/grade-writing`); `05-test` at the 7th session (15 min) → balanced, production-heavy; `05-test` at the 14th session (90 min) → exam-like, sections per skill, multi-format, mirroring a real proficiency test (e.g. Goethe/telc shape).
- **Vocabulary cap — a shared per-session TOTAL.** ~15–30 new vocabulary items per session, logged to the ledger — **mostly the current theme's vocab (the bulk)** plus some high-frequency general words (don't narrow exposure to only the theme). For German, leverage the **English-cognate** items for quick wins but still record full article+plural / verb forms. The cap is the throttle and is **shared** across `/lesson` introductions and `/harvest` (harvest tops up *toward* the cap, never on top of it). It flexes down when the learner reports a large Anki review backlog.
- **Front-load the compressible work; expect the rest to take hours.** The rule-based parts of German (case endings, verb conjugation, word-order rules) compress well for a sharp learner; the exposure-gated parts — vocabulary breadth, listening at native speed, speaking automaticity — do not yield to cleverness. Prioritize input volume and output.
- **At the start of every session, read `STATE.md` first; at the end, update it** (via `/close-day`).
- **Each `/lesson` is one session of advancement (~1.5 h)** — lighter on test sessions.
- **Per-session rotation (the load rule).** A fixed **spine runs every session**: `00-check` (the graded retrieval warm-up that opens the session), `01-vocab`, `02-grammar`, and `04-listening`. **Reading and writing SHARE slot `03`**: exactly one of `03-reading` *or* `03-writing` runs per session (never both), **alternating** one full version each session — run whichever did **not** run last (the authoritative rule; cold start: session 1 = reading). Each may hold **one or more** exercises/tasks. **Grammar advances the roadmap every session.** Listening is the **short staple (~10–15 min)**; the heavier academic segments carry the bulk and **trim, never zero**, so every segment scales to fit 1.5 h.
- **Themes are a second axis, orthogonal to grammar.** The grammar roadmap (`roadmap.md`) is sequenced by difficulty and a theme **never** reorders it. The **current theme** (from `themes.md`, tracked in `STATE.md`) drives (a) the session's new **vocabulary** (the bulk of it) and (b) the **context/topic** of reading (`03-reading`), writing (`03-writing`), listening (`04-listening`), and live speaking. Grammar rides its own track; the theme rides on top supplying vocab + context.
- **Input vs output (critical):** **INPUT** (`03-reading` + `04-listening`) is on the current theme and **may carry grammar above the current roadmap point** — that is welcome (comprehensible input, i+1): **gloss** such structures briefly in Spanish ("esto es el Konjunktiv II — se ve más adelante; capta la idea"), do **not** drill them, and keep the text overall comprehensible. **OUTPUT** (`03-writing` + live speaking) stays **within the grammar taught so far** plus the theme vocab — **never** require the learner to produce a structure not yet taught; a German writing task on the theme must be solvable with the cases/tenses/word-order already covered.
- **Recalibrate against the learner's real data, not the average.** The hours math in §1 is the planning prior; `/recalibrate` overrides it from `scores.csv` + the self-reports.
- **Speaking is done live throughout the session** — there is no speaking segment and no speaking skill. It is still tracked as a skill level; `/close-day` asks a short speaking self-report so `/recalibrate` has a trace.
- **How to practice & self-assess speaking (no skill grades it, so do it yourself):** **shadow** the Easy German / Nicos Weg clips — play a line, then mimic the speaker out loud for rhythm, the ch/umlaut sounds, and final devoicing — and **record yourself and compare against a model**, using **Forvo** (native German recordings of single words — ideal for umlauts and *ch*), **YouGlish** (one German word across many real clips in context), or **Google Translate TTS** as a quick check. This is the loop that turns input into speaking automaticity.

---

## 3. Repository structure

```
language-coach/
├── CLAUDE.md              # constitution (§2) + plan parameters + LISTENING_RESOURCES + German pronunciation note + "read STATE.md first"
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
│   ├── ledger.csv         # single cumulative vocabulary register (upstream of Anki); article+plural / verb forms; optional IPA column
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
│           ├── 00-check/           # EVERY session: the graded retrieval WARM-UP — check.md, answers.md, review.md (/grade)
│           ├── 01-vocab/           # EVERY session: new-words.md (same items appended to vocab/ledger.csv)
│           ├── 02-grammar/         # EVERY session: one folder per topic taught (the backbone)
│           │   └── <topic-slug>/   #   grammar.md (links into grammar/<topic>.md),
│           │                       #   exercise-NN.md, answers-NN.md (learner), review-NN.md (/grade)
│           ├── 03-reading/  OR  03-writing/  # ALTERNATE — exactly ONE per session (never both), one full version each:
│           │                       #   03-reading/: exercise-NN.md (passage + comprehension Qs), answers-NN.md, review-NN.md (/grade)
│           │                       #   03-writing/: task-NN.md (prompt), submission-NN.md, review-NN.md (/grade-writing)
│           ├── 04-listening/       # EVERY session, short: task.md, answers.md (self-check Qs + new-words slot + "how it felt") — SELF-REPORTED, NOT graded, no review.md, not in scores.csv
│           └── 05-test/            # ONLY on cadence (every 7th and every 14th session): test.md, answers.md, review.md
│                                   # speaking is NOT a segment — done live throughout the session (tracked only)
│
└── .claude/
    └── skills/            # SHIP PRE-BUILT — do not recreate
        ├── new-plan/      # SKILL.md + overview-template.md
        ├── lesson/        # SKILL.md
        ├── close-day/     # SKILL.md
        ├── grade/         # SKILL.md
        ├── grade-writing/ # SKILL.md
        ├── recalibrate/   # SKILL.md
        └── harvest/       # SKILL.md (optional)
```

Segments are numbered by the real flow of each session in this fixed order. The **spine** runs every session: `00-check` (the graded retrieval warm-up that opens the session), `01-vocab`, `02-grammar`, `04-listening`. `03-reading` and `03-writing` are two contents of the **same slot `03`** and **alternate** — exactly one per session (never both), one full version each; each may hold **one or more** exercises/tasks. The test (`05-test`) appears **only on cadence** (every 7th and every 14th session). **Speaking is not a segment** — the learner does it live throughout the session; it is tracked as a skill level but never generated. `/lesson` decides depth and creates the numbered segments.

---

## 4. Document model

The **living** files (the system's brain; `/lesson`, `/close-day`, and `/recalibrate` read these first, before planning from memory):

- **`STATE.md`** — the snapshot of *now* (overwritten). Sectioned: current session `N`, estimated level per skill (reading / listening / writing / speaking), current focus, a pointer to the ledger batch, and the **current theme** (its name / index into `themes.md`) with a **sessions-in-theme** count. **Weak spots are not here** — they live in `weak-spots.md`. Read by `/lesson`; written by `/close-day` and `/recalibrate`.
- **`roadmap.md`** — the *grammar topic sequence* (the grammar intent; stable). Generated by `/new-plan` (PHASE 2). Read by `/lesson`; pace adjusted by `/recalibrate`.
- **`themes.md`** — the *theme track* (the theme intent; parallel to `roadmap.md`). An ordered list of the most-frequent everyday-conversation themes, sequenced by **frequency-of-use AND CEFR level** (greetings & self → food → shopping → transport & directions → daily routine → work/school → health → plans & appointments → past experiences → opinions → …). The learner does **not** choose them — they are the high-utility defaults. Each entry carries the theme name, concrete scenarios/sub-topics, a target CEFR band, and key vocab domains. A theme drives the session's vocab + the context of reading/writing/listening/speaking; it **never** reorders grammar. Generated by `/new-plan` (PHASE 2), lightly contextualized to German-speaking culture (the DACH region) but mostly universal. Read by `/lesson`; the current theme is **advanced adaptively** by `/close-day`.
- **`grammar.md`** — the *register* of which topics are covered and their state: **introduced / practicing / mastered**, each transition stamped with **the session number it happened** (e.g. `introduced@N`, `practicing@N`, `mastered@N`). Not a binary checkbox: a topic "seen" but still error-prone (German cases will be exactly this) must be recycled. The transition sessions are load-bearing — `/lesson` uses the least-recently-touched non-active topic for a spaced grammar recycle probe. Read by `/lesson`; written by `/close-day`.
- **`weak-spots.md`** — a single small table tracking churn, session-indexed: `spot | source | category | first_seen_session | last_seen_session | times_recurred | status (active/watch/cleared) | cleared_session`. **`category` is the error TYPE** — for German the useful set is: **gender** (der/die/das), **case** (Nom/Akk/Dat/Gen choice), **adjective-ending**, **word-order** (V2 / verb-final / TeKaMoLo), **verb-conjugation**, **auxiliary** (haben/sein), **separable-prefix**, **tense/aspect**, **preposition** (+ its case), **false-friend**, **spelling** (incl. ß/ss, capitalization of nouns), **word-choice**, **register** — so errors are queryable per-type over time. `/close-day` assigns the category when it adds a new spot (inferred from the `/grade` error pattern) and may refine it on churn. A spot clears only after ≥2 spaced correct reappearances (active → watch → cleared); a re-failure flips it back to active and increments `times_recurred`. Read by `/lesson` (the `00-check` retrieval warm-up is ordered most-churned first); maintained by `/close-day`.
- **`LEARNING-PACE.md`** — **throughput only**: per-segment prescribed vs completed load, self-reported time/difficulty, and one per-segment load multiplier. It carries **no** CEFR / level / roadmap opinion (that is `/recalibrate`'s job). Regenerated by `/close-day` on session 1 and every 3rd session thereafter. Read by `/lesson` (adaptive difficulty) and `/recalibrate`.
- **`vocab/ledger.csv`** — the single vocabulary register (upstream of Anki), with article+plural for nouns, the unpredictable forms for verbs, and an optional IPA column. Read/written by `/lesson` (and `/harvest` if enabled).

**Append-only progress logs** (under `progress/`):

- **`progress/scores.csv`** — one row per graded segment: `session, segment, skill, items, correct, pct, self_difficulty_1to5, tier`. Written by `/grade` and `/grade-writing`; read by `/lesson` for adaptive difficulty (the trailing ~5 rows per skill).
- **`progress/level-history.md`** — one row per `/recalibrate` run: `session N`, CEFR per skill, and what changed and why.

**`progress.md`** (repo root) is **not** a living document — it is a **DERIVED, overwritten human-facing synthesis** snapshot generated on demand by `/progress` (read-only). Distinct from `progress/level-history.md` (the raw, append-only CEFR log written by `/recalibrate`) and from `LEARNING-PACE.md` (tactical per-session throughput consumed by `/lesson`): `progress.md` reads across all of those and the recaps to give the learner a step-back view of the whole journey, and changes none of them. It is regenerated each `/progress` run and is not part of the blank scaffold.

`roadmap.md` (grammar intent) and `grammar.md` (reality) are **not** merged. `/lesson` reads both — one to know what's next, the other to know what's still owed. `themes.md` (theme intent) is the **second, orthogonal axis**: `/lesson` reads the current theme from `STATE.md` to source vocab + the reading/writing/listening context, while grammar advances independently along `roadmap.md`.

**Recaps.** The **root `recap.md`** is a rolling digest of the **last 5 sessions** — regenerated every session by `/close-day` (newest in, 6th-oldest dropped); this is what `/lesson` reads for recent context. Each session also keeps its own **`lessons/session-NNN/recap.md`**, written once by `/close-day` (frontmatter: session `N` + actual duration + scores; **no calendar date**), the permanent per-session record. Both are distinct from `STATE.md`, which is overwritten while the per-session recaps accumulate in git history.

**Reference** (grows; the study material): `grammar/<topic>.md` (the cumulative explanations, linked from each session's grammar segment), `vocab/README.md`. **Work & material:** everything under `lessons/session-NNN/` — `lesson.md` (the plan, **always written**, even on a test-only session) and `class/` with its numbered segments, in this fixed order: `00-check` (the graded retrieval warm-up), `01-vocab`, `02-grammar/<topic-slug>`, then `03-reading` **or** `03-writing` (exactly one per session, alternating, with one or more exercises/tasks), `04-listening` (every session), `05-test` (cadence only). Speaking is not a segment (done live, tracked only).

---

## 5. Skills (index)

The full, authoritative spec for each skill is its own `.claude/skills/<name>/SKILL.md`. They ship pre-built and are plan-agnostic — they read every plan-specific value (content language = Spanish, target language = German, session length = 1.5 h, the German vocabulary conventions, the German listening resources, the support language = English) from `CLAUDE.md`. Summary:

- **`/new-plan`** — this skill: collect parameters, write `overview.md`, build the scaffold (§7), and **generate `roadmap.md` and `themes.md` (PHASE 2)** — the session-sequenced grammar plan and the frequency-and-CEFR-ordered theme track. Run once at the start of a fresh repo.
- **`/lesson`** — create one study session (~1.5 h) under `lessons/session-NNN/`, informed by the root `recap.md` (last-5-session digest). **Adaptive:** it reads the trailing ~5 rows per skill from `progress/scores.csv` plus the `LEARNING-PACE.md` multipliers — 3 consecutive ≥90% on a segment bumps that segment's level; any <70% eases it. It **always writes `lesson.md`** (the plan/overview, opening with a short "por qué hoy" tied to the weak spots, the **current theme**, and the new grammar topic, plus a one-line "la vez pasada" recall) and builds the numbered `class/` segments, scaling each to fit 1.5 h. **Spine every session:** the session **opens with the graded retrieval warm-up `00-check/`** — a ~5–10 min cumulative-retrieval probe built from `weak-spots.md` (ordered most-churned first) plus a spaced grammar-recycle probe (the least-recently-touched non-active topic) and escalation (a re-failed previously-cleared item gets an extra `02-grammar/<topic>/` folder that session); it is a retrieval of *prior* material + active weak spots, never today's new topic — then ~15–30 new vocab items in `01-vocab/new-words.md` (mostly the **current theme's** vocab plus some high-frequency general words; recorded with German article+plural / verb forms; also appended to `vocab/ledger.csv`; the cap is a total shared with `/harvest`), the next grammar topic(s) in `02-grammar/<topic-slug>/` (with `exercise-NN.md`; grammar advances along `roadmap.md` **independent of the theme**), and a short `04-listening/` (~10–15 min on the **current theme**, pointing at the German `LISTENING_RESOURCES` from `CLAUDE.md`, dual-subtitle DE+**English**; offline fallback emits a generic gist+detail + dictation micro-task). **Listening is INPUT** — it may carry grammar above the current roadmap point: gloss briefly (in Spanish), don't drill, keep the clip comprehensible. **Rotating main course in slot `03`:** `03-reading/` and `03-writing/` alternate — exactly one per session (never both; run whichever did **not** run last; session 1 starts with reading), each holding one or more exercises/tasks; both set in the **current theme** and reusing active weak-spot grammar and the last 1–2 sessions' vocab. **Reading is INPUT** (may carry advanced grammar — gloss, don't drill). **Writing is OUTPUT** — within the grammar taught so far plus theme vocab; the task must be solvable with current German (never an untaught case/tense/structure). The writing task is a **concrete CASE / SCENARIO within the current theme** (e.g. theme = restaurant → "escribe un mensaje corto quejándote de que un plato llegó frío y pidiendo una solución"), varied across sessions. The reading material and the writing task each **vary between a conversation/dialogue and a continuous prose text** — rotate for register variety. **Assessments are production-biased** (cloze, transformation, short open answer; MC/TF a deliberate minority per the §2 / `CLAUDE.md` item-format policy, with diagnostic distractors). **`/lesson` generates the answer files as fillable worksheets** alongside each prompt: `00-check/answers.md`, `02-grammar/<topic>/answers-NN.md`, `03-reading/answers-NN.md`, `03-writing/submission-NN.md`, `04-listening/answers.md` (self-check Qs + new-words slot + "cómo se sintió / comprensión auto-evaluada" — self-reported, not graded), and `05-test/answers.md` on a test session. It does **not** build a speaking segment — speaking is done live. A `05-test/` appears **only on cadence**: a 15-minute consolidation test every **7th** session, and a standalone **90-minute test every 14th** (test only, no new teaching). On session 1 (cold start), `lesson.md` also carries the first-run orientation (the loop in 4 steps) and `00-check` becomes a short **level-placement diagnostic** (since the A1 start is an assumption).
- **`/grade`** — grade a test or objective exercise set passed as an argument (no-arg fallback: the most-recent ungraded answers); grades the **objectively-graded** segments only (`00-check`, `02-grammar`, `03-reading`, and tests) — **not `04-listening`, which is self-reported**; corrections with the *why* (e.g. which case the verb governs) plus a recurring-error summary, saved as `review-NN.md` next to the matching `answers` file, **and a row appended to `progress/scores.csv`**. One skill for all test sizes.
- **`/grade-writing`** — holistic writing correction in Spanish with explanations, register notes, and a fully corrected German version. Reads `03-writing/submission-NN.md` and writes `review-NN.md` next to it, **and a row appended to `progress/scores.csv`**. Explicit.
- **`/close-day`** — read this session's `review-NN.md` / `review.md` files (`/grade` and `/grade-writing` output, incl. `00-check/review.md`; listening has no review file) plus the self-report; **maintain `weak-spots.md`** (fold the `00-check` retrieval result into the churn: active→watch→cleared only after ≥2 spaced correct reappearances, re-fail flips back); write `lessons/session-NNN/recap.md` and **regenerate the root `recap.md`** (rolling last-5); record the **grammar transition sessions** in `grammar.md`; **regenerate `LEARNING-PACE.md`** (session 1 and every 3rd session); advance the session counter idempotently; **advance the theme adaptively** — move to the next theme in `themes.md` when its vocab scores are solid, it stops generating new weak spots, and the learner handles its reading/writing without major errors (**guardrails:** stay in a theme **at least ~3** sessions, **at most ~10**); update `STATE.md`'s current-theme and sessions-in-theme; **celebrate** cleared weak spots and newly-mastered topics; ask a **listening + speaking self-report** logged into the recap; refresh `STATE.md`; commit. When the just-closed session `N` is a multiple of 14, it **reminds the learner to run `/recalibrate` next**.
- **`/recalibrate`** — every **14th** session: read the `scores.csv` curve + `weak-spots.md` + recaps + the 90-minute test at `lessons/session-*/class/05-test/review.md`, re-estimate CEFR level per skill — the graded skills (reading / writing / grammar) from `scores.csv`, and the **listening and speaking levels from the `/close-day` self-reports** — adjust the `roadmap.md` pace, update `STATE.md`, and **append a row to `progress/level-history.md`**. **Bonus (optional, light):** if an advanced structure **recurs in the input** across sessions, it MAY flag it as a candidate to **pull forward** in `roadmap.md`. Explicit and **manual**.
- **`/progress`** — a **read-only, on-demand journey synthesis** for the learner, in Spanish. Reads `progress/scores.csv`, `progress/level-history.md`, `weak-spots.md`, recent `lessons/session-*/recap.md` (incl. the listening + speaking self-reports), `STATE.md`, `roadmap.md` + `themes.md`, and `CLAUDE.md`, then produces a step-back view: **per-skill trend & current level** (reading/grammar/writing from `scores.csv`; listening & speaking qualitatively — note the asymmetry), **plateau detection**, **top recurring error categories** (from the `weak-spots.md` category column — for German watch gender/case/word-order), **on-track vs plan** (sessions done vs roadmap/themes against B2/C1 — honestly ahead / on-track / behind, with the realistic A2–B1 framing), **wins / milestones**, and **one actionable suggestion per plateau or sticky error**. It **writes ONLY `progress.md`** and **changes no living document**. **Distinct from `/recalibrate`** (which ACTS); `/progress` only SHOWS. Explicit.
- **`/harvest`** *(optional)* — append the learner's unknown words from a reading to the ledger, correctly formatted (German article+plural / verb forms), **topping up toward the shared per-session vocab cap (never on top of it)**. Can be folded into `/close-day`.

---

## 6. Key decisions & rationale

- **Use real Anki; do not rebuild spaced repetition.** The ledger is upstream, Anki downstream, one-directional. Anki de-duplicates by the **first field** — the canonical headword-with-article defined in §2 (compared case-insensitively, article never stripped) — and both `/lesson` and `/harvest` use that same key, so the CSV is already deduped before import. Scheduling/progress lives **inside Anki**, so re-importing only adds new items and never erases progress. Keep new cards/day ≈ the per-session batch; tag each batch by session; save the CSV as **UTF-8** (so the umlauts and ß survive).
- **Do not fragment skills.** Consolidate when the only difference is a parameter (one `/grade` for all test sizes). A skill earns its place with a **repeatable workflow + file effects**; "explain the German case system" is just talking to Claude.
- **Plan-specifics live in `CLAUDE.md`, logic lives in the skills.** That separation is what lets the skills be invariant and ship pre-built.
- **Hours are the binding constraint.** Test sessions don't also carry a full lesson. For B2/C1 German in 6 months this is the crux — see §1: the target is a stretch, A2–B1 is the realistic, successful landing.
- **Everything is indexed by session number `N`** — no calendar dates, days, weeks, or months as cadence anywhere. (`SESSIONS_PER_WEEK` survives only as the optional hours-estimate input in this `overview.md`.)
- **Weak-spot drilling lives in the graded `00-check` retrieval warm-up** that opens every session and is tracked in `weak-spots.md`, not a separate skill. For German the high-churn categories will be gender, case, and word order.
- **Speaking is done live, not generated** — there is no `/speak` skill; speaking is still tracked as a skill level via the `/close-day` self-report.
- **Keep the skill set small** so descriptions aren't trimmed from context.

---

## 7. Scaffold (built automatically by `/new-plan`)

After writing this file, `/new-plan` builds the rest, then generates `roadmap.md` and `themes.md` (PHASE 2). The skills already exist under `.claude/skills/` and are **not** recreated. What gets created:

1. **`CLAUDE.md`** — the §2 teaching principles, the **plan parameters** (target language = German, content language = Spanish, session length = 1.5 h, target level = B2/C1, duration = 6 months — but **not** `SESSIONS_PER_WEEK`, which is only an optional hours-estimate input here), the German **vocabulary conventions** (article+plural; irregular Präteritum+Partizip II+auxiliary; separable prefixes; governed case; the ledger dedup convention), the German **pronunciation note** (ch ich-/ach-Laut, ä/ö/ü rounding, long/short vowels, the uvular r, z/w/v/s/st-/sp-/sch values, final devoicing, the glottal stop, stem vs separable-prefix stress), the specialized German **listening sources** (`LISTENING_RESOURCES` — Easy German + Nicos Weg + Slow German + DW Langsam gesprochene Nachrichten + Coffee Break German), the **`LISTENING_SUPPORT_LANGUAGE`** (= English), and "read `STATE.md` first."
2. **Blank living docs:** `STATE.md` (current session `N`, level per skill, focus, ledger pointer, current theme = theme 1 + sessions-in-theme = 0), `grammar.md` (empty, with the three-state + transition-session convention), root `recap.md` (placeholder), `weak-spots.md` (header only, the German category set), `LEARNING-PACE.md` (placeholder), `progress/scores.csv` (header row only), `progress/level-history.md` (placeholder), `vocab/ledger.csv` (headers: canonical headword-with-article · gender · plural · meaning(es) · verb forms · optional IPA · example sentence · session tag), `vocab/README.md` (Anki import steps, UTF-8 note).
3. **The folder structure** from §3 (`grammar/`, `vocab/`, `progress/`, `lessons/` — no `recaps/`, `writing/`, `exercises/`, or `assessments/`), with **`.gitkeep`** in the empty scaffolded dirs, and the `.gitignore`.
4. Do **not** recreate the skills in `.claude/skills/` — they already exist (and there is **no** `/speak` skill).
5. **Then generate `roadmap.md` and `themes.md` (PHASE 2)** — `roadmap.md` is the CEFR-tiered, session-sequenced **grammar** plan (A1 → A2 → B1 → B2, the German arc: present tense & the three genders → Nominativ/Akkusativ → Perfekt & separable verbs → Dativ → modal verbs & word order → Präteritum → adjective endings → subordinate clauses & conjunctions → Genitiv → Passiv → Konjunktiv II → relative clauses & extended structures); `themes.md` is the **theme track** (high-utility everyday themes by frequency + CEFR, lightly DACH-contextualized). Do **not** generate lessons or vocabulary yet.
6. If anything is ambiguous, **ask before assuming**.

When the scaffold, `roadmap.md`, and `themes.md` are done, report what was created. The learner's next step is **`/lesson`** to start session 1 (which opens with the level-placement diagnostic).
