# weak-spots — the churn table

> A single small table tracking error churn, session-indexed. Maintained by `/close-day`; read by `/lesson` (the `00-check` retrieval warm-up is ordered most-churned first).
>
> - **category** = the error TYPE (short tag), so errors are queryable per-type over time. For German use tags such as: `gender` (der/die/das), `case` (Nom/Akk/Dat/Gen), `word-order` (V2 / verb-final / TeKaMoLo), `tense/aspect`, `agreement` (adjective endings), `preposition` (incl. two-way Wechselpräpositionen + case), `verb-form` (irregular Präteritum / Partizip II / auxiliary sein vs haben), `separable-prefix`, `false-friend`, `spelling` (incl. ß / umlaut / capitalization of nouns), `word-choice`, `register`.
> - **status** = `active` / `watch` / `cleared`. A spot clears only after ≥2 spaced correct reappearances (active → watch → cleared); a re-failure flips it back to `active` and increments `times_recurred`.
> - `/close-day` assigns the category when it adds a new spot (inferred from the `/grade` error pattern) and may refine it on churn.

| spot | source | category | first_seen_session | last_seen_session | times_recurred | status | cleared_session |
|---|---|---|---|---|---|---|---|
| formas exactas de plural: *Studenten* (n-Dekl.), *Schwestern* (-er→+n), *Zahlen* (fem.→-(e)n, no *Zähler*) | 02-grammar s3 (ej-01 #12, ej-02 #8/#9) | word-form | 3 | 3 | 0 | active |  |
| género/artículo: *der* por defecto (*das Land* → eligió *der*; *die Männer* → *Der*) | 00-check s3 (#8) · 02-grammar s3 (ej-01 #16) | gender | 3 | 3 | 0 | active |  |
| mayúscula de sustantivos (*Familie, Freunde, Buch* en minúscula) | 02-grammar s3 · 03-reading s3 | spelling | 3 | 3 | 0 | active |  |
| número + concordancia: *Meine Muttersprache ist* (no *Muttersprachen ist*) | 03-writing s2 · 00-check s3 (#5, correcto) | agreement | 2 | 3 | 1 | watch |  |
| `die Stadt` (ciudad) vs `das Land` (país) | 02-grammar s2 · 00-check s3 (#9, correcto) | word-choice | 2 | 3 | 1 | watch |  |
| `ist` vs inglés *is* (interferencia) | 02-grammar s2 · 00-check s3 (#10, correcto) | verb-form | 2 | 3 | 1 | watch |  |
| `sein`: `ihr` → `seid` | 02-grammar s1 · 00-check s2,s3 (correcto ×2) | verb-form | 1 | 3 | 1 | cleared | 3 |

> **Churn de la sesión 3:**
> - 🎉 **`ihr seid` → cleared (s1 → s3):** error en s1, correcto en s2 (→watch) y correcto de nuevo en s3 → ≥2 reapariciones correctas espaciadas.
> - **número/concordancia → watch:** 1.ª reaparición correcta (00-check #5 + concordancia plural perfecta en ej-02). Una más y se limpia.
> - **Stadt/Land** e **ist vs is** siguen en **watch** (correctos en s3; una reaparición limpia más para cerrar).
> - **3 nuevos spots (active)** de la s3: morfología exacta de plural, tendencia al artículo *der* por defecto (das Land), y mayúscula de sustantivos.
> - **NO son weak-spots (previews de gramática aún no enseñada):** *spricht* (verbo irregular e→i, roadmap #5) y *meine* posesivo (roadmap #12) — se anotan en el recap, no aquí.
