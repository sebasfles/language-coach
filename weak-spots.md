# weak-spots — the churn table

> A single small table tracking error churn, session-indexed. Maintained by `/close-day`; read by `/lesson` (the `00-check` retrieval warm-up is ordered most-churned first).
>
> - **category** = the error TYPE (short tag), so errors are queryable per-type over time. For German use tags such as: `gender` (der/die/das), `case` (Nom/Akk/Dat/Gen), `word-order` (V2 / verb-final / TeKaMoLo), `tense/aspect`, `agreement` (adjective endings / subject-verb), `preposition`, `verb-form` (irregular / auxiliary / personal endings), `separable-prefix`, `false-friend`, `spelling`, `word-choice`, `register`.
> - **status** = `active` / `watch` / `cleared`. A spot clears only after ≥2 spaced correct reappearances (active → watch → cleared); a re-failure flips it back to `active` and increments `times_recurred`. **Exception — `gender` (lexical der/die/das):** long-haul exposure item, not clear-and-done (see `[[gender-is-long-haul-exposure]]`); recirculate gently, don't penalize.
> - `/close-day` assigns the category when it adds a new spot (inferred from the `/grade` error pattern) and may refine it on churn.

| spot | source | category | first_seen_session | last_seen_session | times_recurred | status | cleared_session |
|---|---|---|---|---|---|---|---|
| **género léxico** (der/die/das por sustantivo) — **EXPOSICIÓN de largo plazo, no penalizar** | 00-check s3–s9 (s9 *die Kassenbon*) · 02-grammar · 03-writing | gender | 3 | 9 | 2 | active |  |
| **definido/indefinido + Akk masc** (*der Saft* → *den Saft*; el/la→der/den) | 05-test s7 · 00-check s8 (✓), s9 (✗ der Saft) | word-choice | 7 | 9 | 1 | active |  |
| concordancia de *du* en **pregunta invertida** (*Kann/Können du* → *Kannst du*) | 02-grammar s8 · 00-check s9 (*Können du*) | verb-form | 8 | 9 | 1 | active |  |
| **-en de más** (masc Akk fuera de sitio): *meinen Schuhe* (pl), *deinen Pullover* (Nom masc), *einen Hose* (fem) | 02-grammar s9 (ej-01 #8/#12) · 03-writing s9 | case | 9 | 9 | 0 | active |  |
| **concordancia con plurales** (*Schuhe* es plural → sin *eine*; verbo *müssen/kosten*) | 03-writing s9 (eine Schuhe; Die Schuhe muss) | agreement | 9 | 9 | 0 | active |  |
| léxico **comprar (kaufen) vs pagar (zahlen)** | 02-grammar s8 · 00-check s9 (✓ kaufe Brot) | word-choice | 8 | 9 | 0 | watch |  |
| `ein-`/`kein-` femenino → **keine** | 02-grammar s6 · 00-check s7,s8,s9 (✓ keine Tüte/Packung ×2) | case | 6 | 9 | 0 | cleared | 9 |
| posición de **nicht** | 03-writing s6 · 00-check s7,s8 | word-order | 6 | 8 | 0 | cleared | 8 |
| `and` → `und` | 03-writing s6 · 00-check/02-grammar s7 | false-friend | 6 | 7 | 0 | cleared | 7 |
| mayúscula de sustantivos | 02-grammar s3 · 03-reading/writing · 00-check s5,s6 | spelling | 3 | 6 | 1 | cleared | 6 |
| formas exactas de plural: *Studenten* | 02-grammar s3 · 00-check s4,s5,s6 | word-form | 3 | 6 | 1 | cleared | 6 |
| terminación verbal según la persona (*fährt/bezahle*) | 02-grammar s4 · 00-check s5,s6 | verb-form | 4 | 6 | 0 | cleared | 6 |
| número + concordancia: *Meine Muttersprache ist* | 03-writing s2 · 00-check s3,s4 | agreement | 2 | 4 | 1 | cleared | 4 |
| `die Stadt` vs `das Land` | 02-grammar s2 · 00-check s3,s4 | word-choice | 2 | 4 | 1 | cleared | 4 |
| `ist` vs inglés *is* | 02-grammar s2 · 00-check s3,s4 | verb-form | 2 | 4 | 1 | cleared | 4 |
| `sein`: `ihr` → `seid` | 02-grammar s1 · 00-check s2,s3 | verb-form | 1 | 3 | 1 | cleared | 3 |

> **Churn de la sesión 9:**
> - 🎉 **`kein-/ein- femenino (keine)` → CLEARED** (s6→s9): keine Tüte + keine Packung ✓✓ (2.ª limpia). ¡Cerrado!
> - 🆕 **-en de más (`case`):** la terminación masc-Akk aplicada a plural (*meinen Schuhe*), Nom masc (*deinen Pullover*) y fem (*einen Hose*). Regla: **-en solo en masc Akkusativo**. Vaivén (en ej-03 lo hizo bien) → drill de automatización.
> - 🆕 **concordancia con plurales (`agreement`):** *Schuhe* es plural → sin *eine*, verbo *müssen* (no *muss*). (Inconsistente: *kosten* sí lo hizo.)
> - 🔁 **du en pregunta invertida → recurre** (*Können du*; s8+s9), tr+1. (Pero *zahlst du* ✓ en la escritura → vaivén.)
> - 🔁 **definido/indefinido + Akk masc → re-activado** (*der Saft* por *den Saft*, 00-check #5), tr+1.
> - ✅ **kaufen vs zahlen → watch** (kaufe Brot correcto).
> - 🟰 **género:** slip *die Kassenbon* (→ der); sigue exposición.
> - **Notas (no weak-spots fijos):** hätte-gern+infinitivo (usar möchte), preposición *in den* con gehen, groß/Größe, registro Sie/du, zehn euros→Euro.
