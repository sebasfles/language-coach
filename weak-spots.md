# weak-spots — the churn table

> A single small table tracking error churn, session-indexed. Maintained by `/close-day`; read by `/lesson` (the `00-check` retrieval warm-up is ordered most-churned first).
>
> - **category** = the error TYPE (short tag), so errors are queryable per-type over time. For German use tags such as: `gender` (der/die/das), `case` (Nom/Akk/Dat/Gen), `word-order` (V2 / verb-final / TeKaMoLo), `tense/aspect`, `agreement` (adjective endings), `preposition` (incl. two-way Wechselpräpositionen + case), `verb-form` (irregular Präteritum / Partizip II / auxiliary sein vs haben), `separable-prefix`, `false-friend`, `spelling` (incl. ß / umlaut / capitalization of nouns), `word-choice`, `register`.
> - **status** = `active` / `watch` / `cleared`. A spot clears only after ≥2 spaced correct reappearances (active → watch → cleared); a re-failure flips it back to `active` and increments `times_recurred`.
> - `/close-day` assigns the category when it adds a new spot (inferred from the `/grade` error pattern) and may refine it on churn.

| spot | source | category | first_seen_session | last_seen_session | times_recurred | status | cleared_session |
|---|---|---|---|---|---|---|---|
| `sein`: `ihr` → `seid` | 02-grammar s1 · 00-check s2 | verb-form | 1 | 2 | 1 | watch |  |
| número + concordancia: *Meine Muttersprache ist* (no *Muttersprachen ist*) | 03-writing s2 | agreement | 2 | 2 | 1 | active |  |
| `die Stadt` (ciudad) vs `das Land` (país) | 02-grammar s2 (prod.) | word-choice | 2 | 2 | 1 | watch |  |
| `ist` vs inglés *is* (interferencia) | 02-grammar s2 (prod.) | verb-form | 2 | 2 | 1 | watch |  |
