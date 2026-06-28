# roadmap.md — Grammar Roadmap (the GRAMMAR INTENT, PHASE 2)

> **What this is.** The ordered **grammar topic sequence** for German (Deutsch), tiered by CEFR band and laid out roughly in teaching order from A1 up to the stated target of **B2/C1**. This is the **intent** — the plan `/lesson` walks to pick the next still-owed grammar topic. It is **separate from `grammar.md`** (the *reality*: the register of what has actually been introduced / practiced / mastered, each transition stamped with the session `N` it happened). `/lesson` reads both — this file to know what's *next*, `grammar.md` to know what's still *owed*.
>
> **Axis.** Grammar is its own track. The **theme** (`themes.md`) is a second, orthogonal axis that supplies vocabulary + the context of reading/writing/listening — a theme **never** reorders this roadmap.
>
> **Indexing.** Everything is indexed by **session number `N`**, never by calendar date, day, week, or month. The session ranges below are **estimates for pacing only**; `/recalibrate` (every 28th session) adjusts the actual pace against the learner's real `scores.csv` curve and weak-spot churn.
>
> **Language rule.** This is a scaffolding/config doc: English structure + field names, German as the content/examples. The daily learner-facing output (`/lesson`) is written in **Spanish** (the content language).

---

## Honest pacing note (read with `overview.md`'s "Honest expectations")

- **Window & budget (assumption).** ~6 months at an **assumed default of ~5 sessions/week** × 1.5 h ≈ **~130 sessions available** (≈ 195 guided hours; the learner will vary sessions/week by progress, so treat ~130 as an estimate, not a contract). Sessions-per-week is an **assumption** used only to size the bands — nothing here is calendar-indexed.
- **B2/C1 in this window is a STRETCH from a near-zero base.** Reaching solid B2 in German typically takes ~600–750 guided hours, more for the exposure-gated skills. A realistic landing in ~195 hours is a **solid A2–B1**, with **reading and grammar leading** and **listening (at native speed) and speaking lagging** — those are gated by exposure hours, not by cleverness. The learner's comfort in **English gives a partial Germanic-cognate bridge** that helps reading/vocabulary somewhat. B2/C1 stays the **north star**, tracked honestly via `LEARNING-PACE.md`, `/progress`, and `/recalibrate` — so a strong A2–B1 result reads as **success**, not failure against an unrealistic number. **Progress is asymmetric.**
- **What this means for the roadmap.** The systematic, rule-based core of German (cases, verb morphology, word order, adjective endings) **compresses well** for a sharp learner and is front-loaded here — expect to move through **A1–A2 grammar within roughly the first ~half** of the program and reach into **B1** grammar by the second half. The **B2 and B2/C1 bands below are aspirational for this window**: they will likely be *introduced as input / glossed* and only *partially drilled* before session ~130 unless `/recalibrate` shows the learner is ahead. **Grammar advancing fast on paper does not equal B2 across all four skills** — automaticity in listening/speaking trails the roadmap.

### Starting point (assumption)

Starting level is assumed **beginner / A1** (not stated by the learner). **Session 1's `00-check` runs a level-placement diagnostic**; `/recalibrate` calibrates from there. If the diagnostic places the learner higher, `/recalibrate` will skip ahead in this roadmap rather than re-teach.

### How the bands map onto the ~130 sessions (estimate)

| Band | Rough session range (estimate) | Realistic status in this window |
|---|---|---|
| **A1** | N ≈ 1–35 | Fully taught + drilled |
| **A2** | N ≈ 30–70 | Fully taught + drilled |
| **B1** | N ≈ 65–110 | Mostly taught; later B1 topics overlap into the tail |
| **B2** | N ≈ 105–130 | Introduced; partially drilled (the realistic frontier) |
| **B2/C1 polish** | N ≈ 125–130+ | Mostly **input / glossed**; full mastery is beyond this window |

Ranges **overlap on purpose** (topics interleave; grammar advances every session but new-topic introduction is lighter on the 7th-session consolidation tests and the standalone 28th-session 90-min test). The numbers are not a schedule — `/recalibrate` re-paces them.

---

## A1 — Foundations (estimate: N ≈ 1–35)

Build the sentence engine: present tense, the article/case system in its first two cases, the verb-second (V2) rule, basic negation and questions, and the Perfekt so the learner can talk about the past from early on.

1. **Sentence basics & word order (V2 rule).** Subject–verb in main clauses; the **finite verb in position 2** (`Heute lerne ich Deutsch.`); subject–verb–object default; the *Satzklammer* (sentence bracket) introduced informally with the first modal/Perfekt.
2. **`sein` and `haben` (present).** The two core irregular verbs; `Ich bin … / Ich habe …`. (Spanish-speaker note: no copula split like *ser/estar* — German has one `sein`.)
3. **Personal pronouns (Nominativ).** `ich, du, er/sie/es, wir, ihr, sie/Sie`; the **formal `Sie`** vs informal `du`.
4. **Regular present tense (conjugation).** `-e/-st/-t/-en/-t/-en` (`machen, wohnen, lernen`); stem ending in `-t/-d` → epenthetic `e` (`arbeiten → du arbeitest`); stem in `-s/-ß/-z` → `du` ends in `-t` (`heißen → du heißt`).
5. **Common irregular / stem-changing present verbs.** Vowel change in `du`/`er`: `e→i` (`sprechen → du sprichst`, `essen → du isst`, `geben → du gibst`), `e→ie` (`sehen → du siehst`, `lesen → du liest`), `a→ä` (`fahren → du fährst`, `schlafen → du schläfst`); high-frequency irregulars `wissen` (`ich weiß`), `nehmen` (`du nimmst`).
6. **Articles & gender — `der/die/das` (Nominativ).** Definite + indefinite (`ein/eine`); **gender is lexical** and must be learned with each noun (ledger convention: record nouns **with article + plural**, e.g. `das Haus, die Häuser`). Common gender-from-ending heuristics (`-ung/-heit/-keit/-tion` → die; `-chen/-lein` → das; many `-er` agent nouns → der) given as tendencies, not laws.
7. **Plural of nouns.** The five-ish plural patterns (`-e`, `-er` + umlaut, `-(e)n`, `-s`, no ending / umlaut only); taught as "memorize per noun" reinforced by the ledger's plural field.
8. **Akkusativ.** The direct-object case; the **only visibly changing article is masculine** `der → den`, `ein → einen` (`Ich habe **einen** Hund.`); `die/das/die-pl` unchanged. Akkusativ personal pronouns (`mich, dich, ihn, sie, es, uns, euch, sie/Sie`).
9. **Negation: `nicht` vs `kein`.** `kein-` negates an indefinite/zero-article noun (`Ich habe **kein** Auto.`); `nicht` negates everything else (verbs, adjectives, definite nouns) — and its **position** (typically late; before the element negated).
10. **W-questions & yes/no questions.** Question words `wer, was, wo, wohin, woher, wann, wie, warum, welch-`; yes/no questions = **verb-first** inversion (`Kommst du?`); answering with `ja / nein / doch`.
11. **Modal verbs (present).** `können, müssen, wollen, sollen, dürfen, mögen` (+ `möchten`); irregular singular forms (`ich kann/muss/will/darf`); the **Satzklammer**: modal in position 2, **infinitive at the end** (`Ich **muss** heute viel **arbeiten**.`).
12. **Possessive articles.** `mein, dein, sein, ihr, unser, euer, ihr/Ihr`; they take **`ein-`-type (kein-) endings** and so already inflect for Nom/Akk + gender.
13. **Imperative.** `du`-form (`Komm! Sprich! Nimm!` — keeps the vowel change, drops `-st`), `ihr`-form (`Kommt!`), formal `Sie`-form (`Kommen Sie!`); the irregular `sei / seid / seien Sie`.
14. **Definite/indefinite & `dieser`/`welcher` (der-words).** `dieser, jeder, welcher` decline like `der` (Nom/Akk for now).
15. **Coordinating conjunctions (no word-order change).** `und, oder, aber, denn, sondern` — **position 0**, they do **not** count for the V2 rule (`Ich bleibe zu Hause, **denn** ich bin müde.`).
16. **Perfekt — introduction (with `haben`).** The everyday past for speech; Satzklammer with the **Partizip II at the end**; regular `ge-…-t` (`gemacht, gekauft`); the most common strong participles by exposure (`gegessen, getrunken, gesehen, gelesen`). (Spanish-speaker note: Perfekt ≈ the spoken past, like *he comido* in usage frequency.)
17. **Perfekt with `sein`.** Verbs of **motion/change of state** (`gehen → ist gegangen`, `kommen → ist gekommen`, `fahren → ist gefahren`, `bleiben → ist geblieben`, plus `sein → ist gewesen`, `werden → ist geworden`); the rule for choosing the auxiliary. Ledger convention: record verbs as `gehen – ging – ist gegangen` (incl. auxiliary).
18. **Numbers, time-telling, dates (grammar of).** Cardinal/ordinal forming; clock time (`um halb acht`, `Viertel nach`); `am`/`um`/`im` time prepositions as set phrases (full two-way prepositions come in A2).
19. **Basic prepositions (high-frequency, by case, as chunks).** Early exposure to a few Akkusativ prepositions (`für, ohne, durch, gegen, um`) and Dativ chunks (`mit, zu, von, bei`) as set phrases — the **full case-governed system is the A2 backbone**.

---

## A2 — The case system completes, the clause opens up (estimate: N ≈ 30–70)

Add the dative, the preposition system (fixed-case + two-way), the full past tenses for speech and the spoken/written narrative split, comparison, and the first subordinate clauses with their verb-final word order.

1. **Dativ — the third case.** The indirect-object case; article forms `dem / der / dem / den (+n on plural noun)`; **dative personal pronouns** (`mir, dir, ihm, ihr, ihm, uns, euch, ihnen, Ihnen`).
2. **Dative verbs.** Verbs that take a dative object (`helfen, danken, gefallen, gehören, antworten, folgen, passen, schmecken`) — flagged because they violate the Spanish-speaker's "object = accusative" expectation (`Ich helfe **dir**`).
3. **Word order with two objects (Dativ + Akkusativ).** Noun order (`Dat before Akk`: `Ich gebe **dem Mann** **das Buch**.`); pronoun reordering (`Akk before Dat` when both are pronouns: `Ich gebe **es ihm**.`); the *Tekamolo* (Te-Ka-Mo-Lo: temporal–kausal–modal–lokal) adverbial order introduced.
4. **Fixed-case prepositions.** **Akkusativ** prepositions (`durch, für, gegen, ohne, um, …`); **Dativ** prepositions (`aus, bei, mit, nach, seit, von, zu, gegenüber`); common contractions (`zum, zur, beim, vom, am, im`).
5. **Two-way prepositions (Wechselpräpositionen).** `an, auf, hinter, in, neben, über, unter, vor, zwischen` — **Akkusativ for direction (wohin?)** vs **Dativ for location (wo?)**; the `legen/liegen, stellen/stehen, setzen/sitzen, hängen` positional-verb pairs.
6. **Perfekt — full system.** Participle formation completed: **separable verbs** (`an|rufen → angerufen`, prefix + `ge` + stem), **inseparable prefixes** (`be-, ver-, er-, ent-, zer-, ge-` → **no `ge-`**: `verstanden, bekommen`), **`-ieren` verbs** (no `ge-`: `studiert, telefoniert`); mixed verbs (`bringen → gebracht`, `denken → gedacht`).
7. **Präteritum of `sein`, `haben`, and the modals.** The simple past forms used even in speech for these high-frequency verbs (`war, hatte, konnte, musste, wollte, sollte, durfte, mochte`); `es gab` (`geben`).
8. **Separable vs inseparable verbs (productive rule).** Separable prefix splits to the end in main clauses (`Ich **rufe** dich morgen **an**.`); inseparable stays attached; stress as the diagnostic (separable = stressed prefix). Ledger convention: write separables as `an|rufen`.
9. **Comparatives & superlatives.** Regular `-er` / `am …-sten` (`schneller, am schnellsten`); umlauting monosyllables (`alt → älter → am ältesten`, `groß, jung, lang`); irregulars `gut → besser → am besten`, `viel → mehr → am meisten`, `gern → lieber → am liebsten`, `hoch → höher`, `nah → näher`; `so … wie` (equality) and `als` (inequality).
10. **Reflexive verbs.** Accusative reflexives (`sich freuen, sich waschen, sich setzen`) and dative reflexives (`sich (etwas) vorstellen, sich die Hände waschen`); reflexive pronoun table; position of the reflexive pronoun.
11. **Subordinate clauses — verb-final word order.** The core A2 leap: subordinating conjunctions send the **finite verb to the END**. Taught in order of usefulness:
    - **`weil`** (because — cause), contrasted with main-clause `denn`;
    - **`dass`** (that — complement clauses);
    - **`wenn`** (if/when — conditional & temporal-repeated);
    - **`als`** (when — single past event) vs `wenn`;
    - **`ob`** (whether — indirect yes/no questions);
    - indirect W-questions (`Ich weiß nicht, **wann** er **kommt**.`).
    Plus the **main-clause-after-subordinate** inversion (subordinate clause in position 1 → finite verb of the main clause comes immediately: `**Weil** ich krank **bin**, **bleibe** ich zu Hause.`).
12. **`werden` for the future (Futur I) — introduction.** `werden + Infinitiv` for intentions/predictions (`Ich **werde** morgen **anrufen**.`), with the everyday note that present tense + time word often covers the future in speech.
13. **Adjective endings — first pass (predicative vs attributive).** Predicative adjectives don't inflect (`Das Haus ist **groß**.`); **attributive** adjectives do — introduce the concept and the **`der`-word (weak) declension in Nom/Akk** as the entry point; full three-table system is B1.
14. **Imperative & polite requests (consolidation).** `Könnten Sie …?`, `Würden Sie …?` as set polite forms (full Konjunktiv II is B1).
15. **Connectors & adverbial linking (A2 set).** `deshalb, deswegen, trotzdem, dann, danach, zuerst, später, also` — note these are **adverbs that take position 1 → inversion** (`Ich bin müde, **deshalb gehe** ich ins Bett.`), distinct from subordinators.

---

## B1 — Precision, register, and the full inflection system (estimate: N ≈ 65–110)

Complete the cases (Genitiv), the adjective-ending tables, relative clauses, the polite/hypothetical mood, the passive, and the written narrative past — the band where German starts to feel "complete."

1. **Adjective endings — the full system.** All three declension patterns across Nom/Akk/Dat/Gen × gender × number:
    - **weak** (after `der`-words),
    - **mixed** (after `ein`-words / possessives / `kein`),
    - **strong** (no preceding article);
    handled as a teachable system with the "where does the case/gender signal live?" rule. This is a multi-session topic and a recurring weak-spot magnet.
2. **Genitiv.** The possessive/relational case; article forms `des/der/des/der` + **`-(e)s` on masc./neut. nouns** (`das Auto **des Mannes**`); the spoken-German `von + Dativ` alternative; **genitive prepositions** (`während, wegen, trotz, (an)statt, innerhalb, außerhalb`), with the note that several take Dativ colloquially.
3. **Relative clauses.** Relative pronouns `der/die/das/die` declined for **gender+number from the antecedent** and **case from the role inside the relative clause** (`Der Mann, **der** dort steht … / **den** ich kenne … / **dem** ich helfe …`); genitive relative `dessen/deren`; **preposition + relative pronoun** (`das Buch, **über das** wir sprechen`); `was` (after `alles/nichts/etwas` and whole-clause antecedents); `wo`-relatives for places.
4. **Konjunktiv II & `würde` (hypothetical / polite).** Present Konjunktiv II: `würde + Infinitiv` as the productive default; the **synthetic forms still used in speech** (`wäre, hätte, könnte, müsste, sollte, wollte, dürfte, gäbe, wüsste`); uses — **polite requests** (`Ich **hätte** gern …`, `**Könnten** Sie …`), **wishes** (`Wenn ich nur mehr Zeit **hätte**!`), **unreal/hypothetical conditionals** (`Wenn ich reich **wäre**, **würde** ich …`); **past Konjunktiv II** (`hätte/wäre + Partizip II`: `Ich **hätte** das nicht **gemacht**.`).
5. **Passiv (Vorgangspassiv).** `werden + Partizip II` in present, Präteritum, and Perfekt (`wird gemacht / wurde gemacht / ist gemacht worden` — note the special `worden`); the **agent with `von`** (and `durch` for means); **passive with modals** (`Das **muss gemacht werden**.`); when/why German prefers the passive (impersonal/process focus).
6. **Präteritum — the narrative past (full).** The written/storytelling simple past for **all** verbs: weak (`-te`: `machte, kaufte`), strong (vowel ablaut: `ging, kam, fuhr, sah, sprach, nahm`), mixed (`brachte, dachte, kannte, wusste`); the **Perfekt vs Präteritum register split** (speech vs writing/narration). Ledger convention already records the strong Präteritum form.
7. **n-Deklension (weak masculine nouns).** Masculine nouns taking **`-(e)n` in all cases except Nom. sg.** (`der Junge → den Jungen`, `der Mensch → den Menschen`, `der Name → den Namen` (+ genitive `-ns`), `der Student, der Herr, der Kunde, der Nachbar`); flagged because it's easily missed.
8. **Connectors — B1 range & two-part conjunctions.** Subordinators `obwohl/obgleich` (concessive), `damit` vs `um … zu` (purpose), `bevor / nachdem` (with the **tense-sequencing** rule: `nachdem` + Plusquamperfekt → main clause Präteritum/Perfekt), `seit(dem)`, `während` (temporal/contrastive), `sodass`; **two-part (correlative) conjunctions** `entweder … oder, weder … noch, sowohl … als auch, nicht nur … sondern auch, zwar … aber, je … desto/umso` (+ the special `je …, desto …` word order).
9. **`um … zu` / `(an)statt … zu` / `ohne … zu` (infinitive clauses with `zu`).** Subject-sharing infinitive constructions (`Ich lerne Deutsch, **um** in Berlin **zu arbeiten**.`); plain `zu + Infinitiv` after certain verbs/adjectives (`Es ist wichtig, pünktlich **zu sein**.`); `zu` placement with separable verbs (`anzurufen`).
10. **Plusquamperfekt.** `hatte/war + Partizip II` for the "past-before-the-past," especially with `nachdem`.
11. **Futur I (consolidation) & Futur II (intro).** Futur I for prediction/assumption (`Er **wird** wohl zu Hause **sein**.` — the **probability** reading, not just future time); brief intro to **Futur II** (`Er **wird** das schon **gemacht haben**.`) for past assumption.
12. **`lassen` and other semi-modals.** `lassen` (let / have-done / leave): `Ich **lasse** mein Auto **reparieren**.`; the modal-like verbs `brauchen … zu`, `scheinen … zu`, `pflegen … zu`; perception verbs + bare infinitive (`Ich **höre** ihn **singen**.`).
13. **Adjective & participle as noun (intro to nominalization).** Nominalized adjectives (`der/die **Deutsche**`, `etwas **Schönes**`, `der **Angestellte**`) — they keep adjective endings; sets up the B2 nominalization work.
14. **Pronominal adverbs (`da(r)-` / `wo(r)-`).** `damit, dafür, darüber, davon …` and the question forms `womit, wofür, worüber …`; the rule that **prepositions referring to things** use `da(r)-`/`wo(r)-`, not the pronoun (`Ich denke **daran**.` not *an es*); ties to **verbs with fixed prepositions** (`warten **auf** + Akk`, `sich freuen **auf/über**`, `denken **an**`, `sich interessieren **für**`).

---

## B2 — Upper intermediate: formal register, complex syntax, nuance (estimate: N ≈ 105–130)

The realistic frontier for this window. These are **introduced and partially drilled**; expect much of B2 to arrive first as **input (reading/listening), glossed**, with full productive control trailing per the honest-expectations note. `/recalibrate` decides how much gets actively drilled before session ~130.

1. **Konjunktiv I — reported / indirect speech.** Forms (`er sei, er habe, er komme, er werde`); the **fallback to Konjunktiv II when K-I = indicative** (`sie haben` → `sie hätten`); tense system of indirect speech (present/past/future reported); register (journalism, formal reporting); `sollen` for hearsay.
2. **Advanced passive & Passiv-Ersatz (passive alternatives).** **Zustandspassiv** (`sein + Partizip II`: `Die Tür **ist geöffnet**.`) vs Vorgangspassiv; passive in all tenses incl. with modals; **passive-replacement constructions**: `sich lassen + Infinitiv` (`Das **lässt sich** leicht **erklären**.`), `sein + zu + Infinitiv` (`Das **ist** zu **erledigen**.`), `-bar`/`-lich` adjectives (`machbar, lesbar`), `man` + active, reflexive `sich`-constructions (`Das Buch **liest sich** gut.`).
3. **Nominalization (Nominalstil).** The shift to noun-heavy formal/academic style: verb → noun (`prüfen → die Prüfung`, `entscheiden → die Entscheidung`), turning subordinate clauses into prepositional noun phrases (`Weil es regnete → **wegen des Regens**`; `Nachdem er angekommen war → **nach seiner Ankunft**`); recognizing and unpacking it (both directions).
4. **Extended participial attributes (erweitertes Partizipialattribut).** The compact pre-noun modifier German loves in written/formal text: present participle (`die **schnell fahrenden** Autos`), past participle (`das **von ihm geschriebene** Buch`), and `zu`-participle / Gerundivum (`die **zu lösende** Aufgabe`); how to expand them into relative clauses and back.
5. **Advanced connectors & word order (Mittelfeld, Negation, focus).** The **Mittelfeld** ordering principles in depth (information structure, given-before-new, pronoun placement, `nicht` placement for sentence vs constituent negation); **conjunctional adverbs** and register-marked connectors (`folglich, infolgedessen, demnach, dennoch, allerdings, jedoch, hingegen, andererseits, somit, nichtsdestotrotz, gleichwohl`); position-1 vs Mittelfeld effects on emphasis; `zwar … aber`, `einerseits … andererseits` at B2 fluency.
6. **Subjunctive nuance / modality of inference.** Subjective use of modal verbs for **degrees of certainty / hearsay** (`Er **muss** zu Hause **sein**.` = must surely be; `Er **dürfte** … = is likely; `Er **soll** … = is said to; `Er **will** … = he claims to; `Er **könnte/mag** …`); `werden` + Infinitiv for assumption; interplay with Futur II for past inference.
7. **Funktionsverbgefüge (light-verb / support-verb constructions).** Fixed noun+verb collocations of formal register: `in Frage **stellen**`, `zur Verfügung **stellen**`, `eine Entscheidung **treffen**`, `Kritik **üben**`, `in Betracht **ziehen**`, `Rücksicht **nehmen** auf`, `zum Ausdruck **bringen**`, `in Anspruch **nehmen**` — taught as recognizable patterns with their everyday-verb paraphrases.
8. **Verbs, adjectives & nouns with fixed prepositions (B2 breadth).** A wider, register-aware inventory of `Verb/Adjektiv/Nomen + Präposition + Kasus` rections (e.g. `bestehen **aus/auf/in**`, `sich handeln **um**`, `teilnehmen **an** + Dat`, `verzichten **auf**`, `stolz **auf**`, `verantwortlich **für**`, `die Frage **nach**`), since these are a persistent productive-accuracy bottleneck.
9. **Word formation & precision.** Productive prefixes/suffixes and their meaning shifts (`ver-, zer-, ent-, be-, er-`; `-ung, -keit, -heit, -nis, -schaft, -tum`), compound nouns (gender/linking elements: `der Arbeit**s**platz`), separable vs inseparable doublets with meaning change (`über**setzen** "ferry across" vs übersetzen "translate"; `um**fahren** vs umfahren`).

---

## B2/C1 polish — register, idiom, complex syntax (estimate: N ≈ 125–130+; mostly INPUT in this window)

Beyond the realistic finish line for ~195 hours — kept here as the **north star** and worked mainly through **comprehensible input** (reading/listening), glossed, not exhaustively drilled. Pull-forward into active drilling only if `/recalibrate` shows the learner is well ahead.

1. **Register & stylistics.** Consciously switching among **colloquial / neutral / formal-written / academic** registers; spoken-German features (`mal, halt, doch, eben, ja, wohl` and the **modal particles** as a system — a notorious gap for learners), ellipsis and colloquial contractions vs written formality.
2. **Idiomatic precision & collocation.** Idioms, fixed expressions, and **natural collocations** (the difference between grammatically correct and idiomatically native); `Redewendungen`, common metaphors, near-synonym discrimination (`Möglichkeit/Gelegenheit/Chance`; `kennen/wissen/können`; `bekommen/erhalten/kriegen`).
3. **Complex / literary syntax.** Long nested sentences with stacked subordinate and relative clauses; fronting and marked word order for emphasis; extended/embedded participial constructions in dense prose; cohesion across paragraphs.
4. **Advanced Konjunktiv & modality.** Full reported-speech control in extended text; Konjunktiv II for diplomatic/hedged register; subtle modal-particle + mood interactions; counterfactual chains.
5. **Genre & text competence.** Argumentation, abstraction, summarizing/paraphrasing at length, formal correspondence and essay conventions — the productive C1 skills that are **hours-gated**, not rule-gated.

---

## Cross-references & how this file is used

- **`/lesson`** walks this roadmap to pick the next still-owed grammar topic each session (grammar advances **every** session), checking it against `grammar.md` (what's actually been introduced/practiced/mastered). The current **theme** (`themes.md` / `STATE.md`) supplies that session's vocabulary and context but **never** reorders this sequence. **OUTPUT** (writing/speaking) stays within grammar taught so far; **INPUT** (reading/listening) may carry structures from **later bands** as comprehensible input — gloss them briefly, don't drill them.
- **`/recalibrate`** (every 28th session) re-paces these bands against the learner's real `scores.csv` curve, weak-spot churn, and the 90-min test — and may **pull a later structure forward** if it keeps recurring in the input and the learner is ready. The session ranges above are estimates; `/recalibrate` is the authority on pace.
- **Honest target.** Per `overview.md`'s honest-expectations section, **B2/C1 is the ambitious north star** for this 6-month window; a **solid A2–B1** (reading/grammar ahead, listening/speaking trailing) is the realistic, *successful* landing. This roadmap front-loads the compressible rule-based grammar precisely so the exposure-gated skills get the remaining hours.
