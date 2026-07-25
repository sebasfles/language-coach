# weak-spots — the churn table

> A single small table tracking error churn, session-indexed. Maintained by `/close-day`; read by `/lesson` (the `00-check` retrieval warm-up is ordered most-churned first).
>
> - **category** = the error TYPE (short tag), so errors are queryable per-type over time. For German use tags such as: `gender` (der/die/das), `case` (Nom/Akk/Dat/Gen), `word-order` (V2 / verb-final / TeKaMoLo), `tense/aspect`, `agreement` (adjective endings / subject-verb), `preposition`, `verb-form` (irregular / auxiliary / personal endings), `separable-prefix`, `false-friend`, `spelling`, `word-choice`, `register`.
> - **status** = `active` / `watch` / `cleared`. A spot clears only after ≥2 spaced correct reappearances (active → watch → cleared); a re-failure flips it back to `active` and increments `times_recurred`. **Exception — `gender` (lexical der/die/das):** long-haul exposure item, not clear-and-done (see `[[gender-is-long-haul-exposure]]`); recirculate gently, don't penalize.
> - `/close-day` assigns the category when it adds a new spot (inferred from the `/grade` error pattern) and may refine it on churn.

| spot | source | category | first_seen_session | last_seen_session | times_recurred | status | cleared_session |
|---|---|---|---|---|---|---|---|
| **género léxico** (der/die/das por sustantivo) — **EXPOSICIÓN de largo plazo, no penalizar** | 00-check s3–s11 (s11 der Bahnhof/das Gleis ✓) · 02-grammar · 03-writing | gender | 3 | 11 | 2 | active |  |
| **-en de más** (añadir -n/-en fuera de masc-Akk): *einen Hose* (fem), **s11 *Zügen*** (plural), *meinen Karte* (fem) | 02-grammar s9 · 03-writing s9,s10 · **00-check s11 (*Zügen*; pero *einen Bus/eine Fahrkarte* ✓)** | case | 9 | 11 | 2 | active |  |
| **`haben` conjugación** (du **hast** / er **hat**) | 03-writing s10 · **00-check s11 (*Habst* ✗) vs escalación s11 (*Hast* ✓)** | verb-form | 10 | 11 | 1 | active |  |
| 🆕 **verbos separables: separación + prefijo** (frase principal → *fährt … ab*; prefijo *ab/an*) | **02-grammar s11 (ej-02 *fährt an*→ab; *aussteige*→steige aus) · 03-writing s11 (*abfahrt*→fährt ab; PERO *Steige … aus* ✓)** | separable-prefix | 11 | 11 | 0 | active |  |
| **`groß` (adj) vs `Größe`** (talla, sustantivo) | 03-writing s10 (*mit große* ×2) | word-choice | 10 | 10 | 0 | active |  |
| **pronombre en imperativo con `Sie`** (posición *Helfen Sie mir*; + omisión de *mir*) | 02-grammar s10 (ej-02/ej-03) | word-order | 10 | 10 | 0 | active |  |
| **`sein`: `ihr` → seid** — recuperándose (recaída s10 *Seind*) | 00-check s2,s3 (cleared@3) · s10 (*Seind* ✗) · **escalación s11 (*Seid ihr müde?* ✓)** | verb-form | 1 | 11 | 1 | watch |  |
| **`kein-`/`ein-` femenino → keine** — recuperándose (recaída s10 *kein Hose*) | 02-grammar s6 · cleared@9 · s10 (*kein Hose* ✗) · **00-check s11 (*keine Zeit* ✓)** | case | 6 | 11 | 1 | watch |  |
| **definido/indefinido + Akk masc** (*der Saft*→*den*; *dieser*→*diesen*) | 05-test s7 · 00-check s8✓,s9✗,s10✓ · **02-grammar s11 (diesen/welchen/jeden ✓; 1 desliz *dieser* ej-02 #1)** | word-choice | 7 | 11 | 1 | watch |  |
| concordancia de *du* en **pregunta invertida** (*Kannst du*) | 02-grammar s8 · 00-check s9✗,s10✓ | verb-form | 8 | 10 | 1 | watch |  |
| **concordancia con plurales** (*Schuhe* → sin *eine*; verbo plural) | 03-writing s9 · 00-check s10✓ | agreement | 9 | 10 | 0 | watch |  |
| léxico **comprar (kaufen) vs pagar (zahlen)** | 02-grammar s8 · 00-check s9✓ · 03-writing s10✓ | word-choice | 8 | 10 | 0 | cleared | 10 |
| posición de **nicht** | 03-writing s6 · 00-check s7,s8 | word-order | 6 | 8 | 0 | cleared | 8 |
| `and` → `und` | 03-writing s6 · 00-check/02-grammar s7 | false-friend | 6 | 7 | 0 | cleared | 7 |
| mayúscula de sustantivos | 02-grammar s3 · 00-check s5,s6 | spelling | 3 | 6 | 1 | cleared | 6 |
| formas exactas de plural: *Studenten* | 02-grammar s3 · 00-check s4,s5,s6 | word-form | 3 | 6 | 1 | cleared | 6 |
| terminación verbal según la persona (*fährt/bezahle*) | 02-grammar s4 · 00-check s5,s6 | verb-form | 4 | 6 | 0 | cleared | 6 |
| número + concordancia: *Meine Muttersprache ist* | 03-writing s2 · 00-check s3,s4 | agreement | 2 | 4 | 1 | cleared | 4 |
| `die Stadt` vs `das Land` | 02-grammar s2 · 00-check s3,s4 | word-choice | 2 | 4 | 1 | cleared | 4 |
| `ist` vs inglés *is* | 02-grammar s2 · 00-check s3,s4 | verb-form | 2 | 4 | 1 | cleared | 4 |

> **Churn de la sesión 11:**
> - 🆕 **verbos separables** (`separable-prefix`) — **el punto central de hoy** (tema Verkehr, lleno de ellos). Mixto: mal en ej-02 (*fährt an*, *aussteige*) y writing-01 (*abfahrt*), **pero BIEN en writing-02 (*Steige … aus* ✓)** tras la charla. Regla a automatizar: en frase principal **el verbo se conjuga y el prefijo va al final** (*fährt … ab*); con modal, entero (*muss abfahren*).
> - ✅ **Dos → `watch`** (1.ª limpia tras la recaída): **`ihr seid`** (escalación *Seid ihr müde?* ✓) y **`keine` femenino** (*keine Zeit* ✓). Una más y cierran.
> - 🟰 **`haben`** — **mixto en la misma sesión**: 00-check *Habst* ✗ / escalación *Hast* ✓. Lo sabe con foco, se cae bajo prisa → sigue `active`, tr→1.
> - 🟰 **-en de más** — el reflejo se **movió al plural**: *Zügen* (por *Züge*), aunque la forma de artículo (*einen Bus/eine Fahrkarte*) salió **bien**. tr→2, sigue `active`.
> - 🟰 **der→den** (watch): *diesen/welchen/jeden* correctos (dieser-welcher), 1 desliz suelto (*dieser* ej-02 #1) → se mantiene en `watch` (evidencia dominante correcta).
> - 🟰 **género** correcto s11 (Bahnhof/Gleis) — exposición estable.
> - **Notas (no weak-spots fijos):** *du muss→musst* (modal en du, -st) — 1 caso, vigilar (ver grammar.md modalverben); *fahrt→fährt* (vokalwechsel, 1 desliz en respuesta de lectura); **A2/B1 reaches NO penalizados** — *warten auf* + Akk (*auf den Bus / auf dich*), *mit* + Dativo (*mit diesem/meiner*), oración de relativo (*der Bus, den du nimmst*) — el learner los intentó y preguntó; aclarados, candidatos a input glosado.
