# weak-spots — the churn table

> A single small table tracking error churn, session-indexed. Maintained by `/close-day`; read by `/lesson` (the `00-check` retrieval warm-up is ordered most-churned first).
>
> - **category** = the error TYPE (short tag), so errors are queryable per-type over time. For German use tags such as: `gender` (der/die/das), `case` (Nom/Akk/Dat/Gen), `word-order` (V2 / verb-final / TeKaMoLo), `tense/aspect`, `agreement` (adjective endings), `preposition` (incl. two-way Wechselpräpositionen + case), `verb-form` (irregular Präteritum / Partizip II / auxiliary sein vs haben / personal endings), `separable-prefix`, `false-friend`, `spelling` (incl. ß / umlaut / capitalization of nouns), `word-choice`, `register`.
> - **status** = `active` / `watch` / `cleared`. A spot clears only after ≥2 spaced correct reappearances (active → watch → cleared); a re-failure flips it back to `active` and increments `times_recurred`. **Exception — `gender` (lexical der/die/das):** treated as a **long-haul exposure item**, not clear-and-done (see `[[gender-is-long-haul-exposure]]`); recirculate gently, don't penalize as a rule error, don't expect `cleared` soon.
> - `/close-day` assigns the category when it adds a new spot (inferred from the `/grade` error pattern) and may refine it on churn.

| spot | source | category | first_seen_session | last_seen_session | times_recurred | status | cleared_session |
|---|---|---|---|---|---|---|---|
| **género léxico** (der/die/das por sustantivo): *die Käse*→der; *Das Suppe*→die (00-check ✓, falla en producción) — **EXPOSICIÓN de largo plazo, no penalizar** | 00-check s3–s6 · 02-grammar s3,s5,s6 · 03-writing s4,s6 | gender | 3 | 6 | 2 | active |  |
| `ein-`/`kein-` femenino → **keine** (terminación, no *kein*/*keinen*) | 02-grammar s6 (ej-01 #3/#5) | case | 6 | 6 | 0 | active |  |
| posición de **nicht** (antes del adjetivo/adverbio: *nicht vegetarisch*) | 03-writing s6 (task-01) | word-order | 6 | 6 | 0 | active |  |
| `and` → `und` (interferencia del inglés) | 03-writing s6 (task-02, autocorregido) | false-friend | 6 | 6 | 0 | watch |  |
| mayúscula de sustantivos | 02-grammar s3 · 03-reading s3 · 03-writing s4 · 00-check s5,s6 · 03-writing s6 (✓×2) | spelling | 3 | 6 | 1 | cleared | 6 |
| formas exactas de plural: *Studenten* (n-Dekl.) | 02-grammar s3 · 00-check s4,s5,s6 (✓×2) | word-form | 3 | 6 | 1 | cleared | 6 |
| terminación verbal según la persona (*fährt*, *bezahle*) | 02-grammar s4 · 03-writing s4 · 00-check s5,s6 (✓×2) | verb-form | 4 | 6 | 0 | cleared | 6 |
| número + concordancia: *Meine Muttersprache ist* | 03-writing s2 · 00-check s3,s4 | agreement | 2 | 4 | 1 | cleared | 4 |
| `die Stadt` (ciudad) vs `das Land` (país) | 02-grammar s2 · 00-check s3,s4 | word-choice | 2 | 4 | 1 | cleared | 4 |
| `ist` vs inglés *is* (interferencia) | 02-grammar s2 · 00-check s3,s4 | verb-form | 2 | 4 | 1 | cleared | 4 |
| `sein`: `ihr` → `seid` | 02-grammar s1 · 00-check s2,s3 | verb-form | 1 | 3 | 1 | cleared | 3 |

> **Churn de la sesión 6:**
> - 🎉 **3 spots → cleared (2.ª reaparición correcta en el 00-check + producción):** **mayúscula** (s3→s6; confirmada en escritura libre 5/5), **plural exacto** (s3→s6; *die Studenten* ✓×2), **terminación verbal** (s4→s6; *fährt/bezahle* ✓×2).
> - 🔁 **género léxico → RECLASIFICADO como EXPOSICIÓN de largo plazo (sigue active, tr 2):** correcto en el 00-check y el mini-texto, pero falla en producción libre (*die Käse*, *Das Suppe*). Por decisión del learner (correcta): **recircular suave, NO penalizar como regla, no forzar `cleared`**. Ver `[[gender-is-long-haul-exposure]]`.
> - 🆕 **kein-/ein- femenino → keine** (`case`): regla drillable (fem lleva -e), distinta del género léxico. Es la parte *arreglable*.
> - 🆕 **posición de nicht** (`word-order`): *nicht* va antes del adjetivo/adverbio que niega.
> - 🆕 **and→und** (`false-friend`, watch): interferencia del inglés; autocorregida al señalarla → watch, no active.
