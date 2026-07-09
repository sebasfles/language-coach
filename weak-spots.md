# weak-spots — the churn table

> A single small table tracking error churn, session-indexed. Maintained by `/close-day`; read by `/lesson` (the `00-check` retrieval warm-up is ordered most-churned first).
>
> - **category** = the error TYPE (short tag), so errors are queryable per-type over time. For German use tags such as: `gender` (der/die/das), `case` (Nom/Akk/Dat/Gen), `word-order` (V2 / verb-final / TeKaMoLo), `tense/aspect`, `agreement` (adjective endings), `preposition` (incl. two-way Wechselpräpositionen + case), `verb-form` (irregular Präteritum / Partizip II / auxiliary sein vs haben / personal endings), `separable-prefix`, `false-friend`, `spelling` (incl. ß / umlaut / capitalization of nouns), `word-choice`, `register`.
> - **status** = `active` / `watch` / `cleared`. A spot clears only after ≥2 spaced correct reappearances (active → watch → cleared); a re-failure flips it back to `active` and increments `times_recurred`. **Exception — `gender` (lexical der/die/das):** treated as a **long-haul exposure item**, not clear-and-done (see `[[gender-is-long-haul-exposure]]`); recirculate gently, don't penalize as a rule error, don't expect `cleared` soon.
> - `/close-day` assigns the category when it adds a new spot (inferred from the `/grade` error pattern) and may refine it on churn.

| spot | source | category | first_seen_session | last_seen_session | times_recurred | status | cleared_session |
|---|---|---|---|---|---|---|---|
| **género léxico** (der/die/das por sustantivo) — **EXPOSICIÓN de largo plazo, no penalizar** | 00-check s3–s7 · 02-grammar s3,s5,s6 · 03-writing s4,s6 | gender | 3 | 7 | 2 | active |  |
| `ein-`/`kein-` femenino → **keine/eine** (terminación) — *aún sin probar limpio* | 02-grammar s6 (ej-01 #3/#5) · 00-check s7 (consigna ambigua) | case | 6 | 6 | 0 | active |  |
| **definido vs indefinido** (el/la→der/den vs un/una→ein/einen) | 05-test s7 (#9 *einen* por *den*); asomó s5 | word-choice | 7 | 7 | 0 | watch |  |
| posición de **nicht** (antes del adjetivo/adverbio) | 03-writing s6 · 00-check s7 (✓) | word-order | 6 | 7 | 0 | watch |  |
| `and` → `und` (interferencia del inglés) | 03-writing s6 · 00-check s7 + 02-grammar s7 (✓×2) | false-friend | 6 | 7 | 0 | cleared | 7 |
| mayúscula de sustantivos | 02-grammar s3 · 03-reading s3 · 03-writing s4,s6 · 00-check s5,s6 | spelling | 3 | 6 | 1 | cleared | 6 |
| formas exactas de plural: *Studenten* (n-Dekl.) | 02-grammar s3 · 00-check s4,s5,s6 | word-form | 3 | 6 | 1 | cleared | 6 |
| terminación verbal según la persona (*fährt*, *bezahle*) | 02-grammar s4 · 03-writing s4 · 00-check s5,s6 | verb-form | 4 | 6 | 0 | cleared | 6 |
| número + concordancia: *Meine Muttersprache ist* | 03-writing s2 · 00-check s3,s4 | agreement | 2 | 4 | 1 | cleared | 4 |
| `die Stadt` (ciudad) vs `das Land` (país) | 02-grammar s2 · 00-check s3,s4 | word-choice | 2 | 4 | 1 | cleared | 4 |
| `ist` vs inglés *is* (interferencia) | 02-grammar s2 · 00-check s3,s4 | verb-form | 2 | 4 | 1 | cleared | 4 |
| `sein`: `ihr` → `seid` | 02-grammar s1 · 00-check s2,s3 | verb-form | 1 | 3 | 1 | cleared | 3 |

> **Churn de la sesión 7:**
> - 🎉 **`and→und` → cleared (s6→s7):** correcto sin ayuda en 00-check + varias veces en el ejercicio de conjunciones.
> - ✅ **posición de nicht → watch** (correcto en 00-check: *nicht vegetarisch*). Una reaparición limpia más → cleared.
> - 🆕 **definido vs indefinido → watch** (test #9: *einen* por *den*; "el"→den). Leve; el caso está bien, es la elección el/un.
> - 🔁 **kein- femenino (keine) → sigue active, SIN probar limpio** (la consigna del 00-check fue ambigua → el learner escribió *eine*; el test no tenía ítem femenino de kein-). Re-probar con consigna clara.
> - 🟰 **género léxico:** **correcto** esta sesión (der Käse, einen Käse, die Suppe…). Sigue como **exposición de largo plazo** (active, sin penalizar); buena señal de exposición.
> - **TEST 94%** confirma que el arco A1 (verbos, Nom, plural, Akk, negación) está firme.
