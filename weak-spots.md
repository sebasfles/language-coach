# weak-spots — the churn table

> A single small table tracking error churn, session-indexed. Maintained by `/close-day`; read by `/lesson` (the `00-check` retrieval warm-up is ordered most-churned first).
>
> - **category** = the error TYPE (short tag), so errors are queryable per-type over time. For German use tags such as: `gender` (der/die/das), `case` (Nom/Akk/Dat/Gen), `word-order` (V2 / verb-final / TeKaMoLo), `tense/aspect`, `agreement` (adjective endings), `preposition` (incl. two-way Wechselpräpositionen + case), `verb-form` (irregular Präteritum / Partizip II / auxiliary sein vs haben / personal endings), `separable-prefix`, `false-friend`, `spelling` (incl. ß / umlaut / capitalization of nouns), `word-choice`, `register`.
> - **status** = `active` / `watch` / `cleared`. A spot clears only after ≥2 spaced correct reappearances (active → watch → cleared); a re-failure flips it back to `active` and increments `times_recurred`.
> - `/close-day` assigns the category when it adds a new spot (inferred from the `/grade` error pattern) and may refine it on churn.

| spot | source | category | first_seen_session | last_seen_session | times_recurred | status | cleared_session |
|---|---|---|---|---|---|---|---|
| género/artículo: género no automático (*Buch*, *Essen*; en s5 ambos ✓) | 00-check s3,s4,s5 · 02-grammar s3,s5 · 03-writing s4 | gender | 3 | 5 | 1 | watch |  |
| mayúscula de sustantivos (*die rechnung* s4; ✓ en 00-check s5, falta confirmar en producción) | 02-grammar s3 · 03-reading s3 · 03-writing s4 · 00-check s5 | spelling | 3 | 5 | 1 | watch |  |
| formas exactas de plural: *Studenten* (n-Dekl.); en s5 ✓ | 02-grammar s3 · 00-check s4,s5 | word-form | 3 | 5 | 1 | watch |  |
| terminación verbal según la persona (*fährt*, *bezahle*; en s5 ambos ✓) | 02-grammar s4 · 03-writing s4 · 00-check s5 | verb-form | 4 | 5 | 0 | watch |  |
| número + concordancia: *Meine Muttersprache ist* | 03-writing s2 · 00-check s3,s4 | agreement | 2 | 4 | 1 | cleared | 4 |
| `die Stadt` (ciudad) vs `das Land` (país) | 02-grammar s2 · 00-check s3,s4 | word-choice | 2 | 4 | 1 | cleared | 4 |
| `ist` vs inglés *is* (interferencia) | 02-grammar s2 · 00-check s3,s4 | verb-form | 2 | 4 | 1 | cleared | 4 |
| `sein`: `ihr` → `seid` | 02-grammar s1 · 00-check s2,s3 | verb-form | 1 | 3 | 1 | cleared | 3 |

> **Churn de la sesión 5:**
> - 🎯 **TODOS los weak-spots activos → watch** (1.ª reaparición correcta espaciada; todos salieron bien en el 00-check y la gramática):
>   - **género/artículo:** *das Buch* ✓ + *das Essen* ✓ (los que fallaron en s4) → active → **watch**.
>   - **terminación verbal:** *fährt* ✓ + *bezahle* ✓ → active → **watch**.
>   - **plural exacto:** *die Studenten* ✓ (el último que resistía) → active → **watch**.
>   - **mayúscula de sustantivos:** ✓ en el 00-check → active → **watch**; ⚠️ **confirmar en producción libre** (en s4 falló en escritura; la s6 toca escritura).
> - **Una reaparición correcta más cada uno → cleared.**
> - **Sin nuevos spots.** Los deslices de la s5 (bezhale, un, moecht, 2 typos en traducción) fueron **erratas de tecleo**, aclaradas — no patrones.
