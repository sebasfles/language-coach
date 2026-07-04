# weak-spots — the churn table

> A single small table tracking error churn, session-indexed. Maintained by `/close-day`; read by `/lesson` (the `00-check` retrieval warm-up is ordered most-churned first).
>
> - **category** = the error TYPE (short tag), so errors are queryable per-type over time. For German use tags such as: `gender` (der/die/das), `case` (Nom/Akk/Dat/Gen), `word-order` (V2 / verb-final / TeKaMoLo), `tense/aspect`, `agreement` (adjective endings), `preposition` (incl. two-way Wechselpräpositionen + case), `verb-form` (irregular Präteritum / Partizip II / auxiliary sein vs haben / personal endings), `separable-prefix`, `false-friend`, `spelling` (incl. ß / umlaut / capitalization of nouns), `word-choice`, `register`.
> - **status** = `active` / `watch` / `cleared`. A spot clears only after ≥2 spaced correct reappearances (active → watch → cleared); a re-failure flips it back to `active` and increments `times_recurred`.
> - `/close-day` assigns the category when it adds a new spot (inferred from the `/grade` error pattern) and may refine it on churn.

| spot | source | category | first_seen_session | last_seen_session | times_recurred | status | cleared_session |
|---|---|---|---|---|---|---|---|
| género/artículo: género no automático (*das Buch*→eligió *der*; *das Essen*→escribió *die*; *das Land* ya ✓) | 00-check s3,s4 · 02-grammar s3 · 03-writing s4 | gender | 3 | 4 | 1 | active |  |
| terminación verbal según la persona (*Er fähre*→*fährt*; *Ich bezahlen*→*bezahle*) | 02-grammar s4 · 03-writing s4 | verb-form | 4 | 4 | 0 | active |  |
| formas exactas de plural: *Studente*→*Studenten* (n-Dekl.); *Schwestern*/*Zahlen* ya ✓ | 02-grammar s3 · 00-check s4 | word-form | 3 | 4 | 1 | active |  |
| mayúscula de sustantivos (*die rechnung* en producción; correcto en 00-check) | 02-grammar s3 · 03-reading s3 · 03-writing s4 | spelling | 3 | 4 | 1 | active |  |
| número + concordancia: *Meine Muttersprache ist* | 03-writing s2 · 00-check s3,s4 (correcto ×2) | agreement | 2 | 4 | 1 | cleared | 4 |
| `die Stadt` (ciudad) vs `das Land` (país) | 02-grammar s2 · 00-check s3,s4 (correcto ×2) | word-choice | 2 | 4 | 1 | cleared | 4 |
| `ist` vs inglés *is* (interferencia) | 02-grammar s2 · 00-check s3,s4 (correcto ×2) | verb-form | 2 | 4 | 1 | cleared | 4 |
| `sein`: `ihr` → `seid` | 02-grammar s1 · 00-check s2,s3 (correcto ×2) | verb-form | 1 | 3 | 1 | cleared | 3 |

> **Churn de la sesión 4:**
> - 🎉 **3 spots → cleared (s2 → s4):** número/concordancia (#8 00-check correcto), Stadt/Land (#9 correcto) e ist vs is (#10 correcto) — 2.ª reaparición correcta espaciada cada uno.
> - 🔁 **género/artículo → sigue active, `times_recurred`+1:** *das Land* ya correcto, pero recurrió en *das Buch* (eligió *der*) y *das Essen* (escribió *die*). El género sigue sin ser automático → **punto #1 a machacar**.
> - 🔁 **plural exacto → active, +1:** *Studenten* (n-Dekl.) aún resiste (Schwestern/Zahlen ya resueltos).
> - 🔁 **mayúscula de sustantivos → active, +1:** correcta en el 00-check pero falló en producción libre (*die rechnung*).
> - 🆕 **terminación verbal según la persona (active):** *fähre→fährt* (ej-02) y *bezahlen→bezahle* (escritura) — que la terminación remate según la persona (‑e ich / ‑t er·sie·es).
> - **NO son weak-spots:** *aber* (conector nuevo, va al ledger), y erratas sueltas de tecleo (*empfielht, Spaniesch*).
