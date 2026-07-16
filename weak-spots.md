# weak-spots — the churn table

> A single small table tracking error churn, session-indexed. Maintained by `/close-day`; read by `/lesson` (the `00-check` retrieval warm-up is ordered most-churned first).
>
> - **category** = the error TYPE (short tag), so errors are queryable per-type over time. For German use tags such as: `gender` (der/die/das), `case` (Nom/Akk/Dat/Gen), `word-order` (V2 / verb-final / TeKaMoLo), `tense/aspect`, `agreement` (adjective endings / subject-verb), `preposition`, `verb-form` (irregular / auxiliary / personal endings), `separable-prefix`, `false-friend`, `spelling`, `word-choice`, `register`.
> - **status** = `active` / `watch` / `cleared`. A spot clears only after ≥2 spaced correct reappearances (active → watch → cleared); a re-failure flips it back to `active` and increments `times_recurred`. **Exception — `gender` (lexical der/die/das):** long-haul exposure item, not clear-and-done (see `[[gender-is-long-haul-exposure]]`); recirculate gently, don't penalize.
> - `/close-day` assigns the category when it adds a new spot (inferred from the `/grade` error pattern) and may refine it on churn.

| spot | source | category | first_seen_session | last_seen_session | times_recurred | status | cleared_session |
|---|---|---|---|---|---|---|---|
| **`sein`: `ihr` → seid** (s10 *Seind*) — **RECAÍDA** (estaba cleared@3) | 02-grammar s1 · 00-check s2,s3 (cleared@3) · **00-check s10 (*Seind*)** | verb-form | 1 | 10 | 1 | active |  |
| **género léxico** (der/die/das por sustantivo) — **EXPOSICIÓN de largo plazo, no penalizar** | 00-check s3–s10 (s10 *die Angebot*→das) · 02-grammar · 03-writing | gender | 3 | 10 | 2 | active |  |
| **-en de más** (masc Akk fuera de sitio): *meinen Schuhe*, *deinen Pullover*, *einen Hose* (fem) | 02-grammar s9 · 03-writing s9 · **02-grammar s10 (*einen Hose*, ej-03)** | case | 9 | 10 | 1 | active |  |
| **`kein-`/`ein-` femenino → keine** (s10 *kein Hose*) — **RECAÍDA** (estaba cleared@9) | 02-grammar s6 · 00-check s7,s8,s9 (cleared@9) · **03-writing s10 (*kein Hose*)** | case | 6 | 10 | 1 | active |  |
| **`haben` conjugación** (du **hast** / er **hat**; s10 *habst*, *habt*) | 03-writing s10 (*Du habst*, *die Jacke habt*) | verb-form | 10 | 10 | 0 | active |  |
| **`groß` (adj) vs `Größe`** (talla, sustantivo) | 03-writing s10 (*mit große* ×2 → *in Größe*) · nota s9 | word-choice | 10 | 10 | 0 | active |  |
| **pronombre en imperativo con `Sie`** (posición: *Helfen Sie mir*; + omisión de *mir*) | 02-grammar s10 (ej-02 *Helfen mir Sie*; ej-03 *Zeig ø die Schuhe*) | word-order | 10 | 10 | 0 | active |  |
| **definido/indefinido + Akk masc** (*der Saft*→*den*) | 05-test s7 · 00-check s8✓,s9✗,**s10✓** (*den Saft*, *den Kassenbon*) | word-choice | 7 | 10 | 1 | watch |  |
| concordancia de *du* en **pregunta invertida** (*Kannst du*) | 02-grammar s8 · 00-check s9✗,**s10✓** (*Kannst du*) | verb-form | 8 | 10 | 1 | watch |  |
| **concordancia con plurales** (*Schuhe* → sin *eine*; verbo plural) | 03-writing s9 · **00-check s10✓** (*Schuhe kosten*) · ej-03 (Schuhe→Schuh) | agreement | 9 | 10 | 0 | watch |  |
| léxico **comprar (kaufen) vs pagar (zahlen)** | 02-grammar s8 · 00-check s9✓ · **03-writing s10✓** (*Zahl mit Karte*) | word-choice | 8 | 10 | 0 | cleared | 10 |
| posición de **nicht** | 03-writing s6 · 00-check s7,s8 | word-order | 6 | 8 | 0 | cleared | 8 |
| `and` → `und` | 03-writing s6 · 00-check/02-grammar s7 | false-friend | 6 | 7 | 0 | cleared | 7 |
| mayúscula de sustantivos | 02-grammar s3 · 03-reading/writing · 00-check s5,s6 | spelling | 3 | 6 | 1 | cleared | 6 |
| formas exactas de plural: *Studenten* | 02-grammar s3 · 00-check s4,s5,s6 | word-form | 3 | 6 | 1 | cleared | 6 |
| terminación verbal según la persona (*fährt/bezahle*) | 02-grammar s4 · 00-check s5,s6 | verb-form | 4 | 6 | 0 | cleared | 6 |
| número + concordancia: *Meine Muttersprache ist* | 03-writing s2 · 00-check s3,s4 | agreement | 2 | 4 | 1 | cleared | 4 |
| `die Stadt` vs `das Land` | 02-grammar s2 · 00-check s3,s4 | word-choice | 2 | 4 | 1 | cleared | 4 |
| `ist` vs inglés *is* | 02-grammar s2 · 00-check s3,s4 | verb-form | 2 | 4 | 1 | cleared | 4 |

> **Churn de la sesión 10:**
> - 🎉 **`kaufen` vs `zahlen` → CLEARED** (s8→s10): *kaufe Brot* (s9) + *Zahl mit Karte* (s10) ✓✓.
> - ✅ **Tres puntos activos → `watch`** (1.ª aparición correcta tras el fallo): **der→den** (*den Saft/den Kassenbon* ✓), **du en pregunta** (*Kannst du* ✓), **concordancia con plurales** (*Schuhe kosten* ✓). Una limpia más y cierran.
> - 🔁🔻 **DOS RECAÍDAS de puntos ya cerrados** (regla de regresión → vuelven a `active`, tr++):
>   - **`sein: ihr → seid`** (cleared@3) → *Seind ihr müde?* en el 00-check. Era también el **sondeo espaciado** de `praesens-sein-personalpronomen` → demota ese tema a `practicing@10` (ver grammar.md).
>   - **`keine` femenino** (cleared@9) → *kein Hose* en escritura. **Matiz:** en la misma nota escribió *eine Hose* (ein- fem) bien → parece caída de la *-e* por prisa. Vigilar sin dramatizar.
> - 🆕 **Nuevos:** **`haben` conjugación** (habst/habt→hast/hat) `verb-form`; **`groß` vs `Größe`** `word-choice`; **pronombre en imperativo con `Sie`** (Helfen Sie mir; y omisión de *mir*) `word-order`.
> - 🟰 **-en de más** recurre (*einen Hose*), sigue `active`, tr→1 — el punto más persistente ahora.
> - 🟰 **género** sigue exposición (*die Angebot*→das).
> - **Notas (no weak-spots fijos):** *Wart→Warte* (la -e obligatoria tras -t) queda dentro de `imperativ practicing@10`; léxico *carrito = der Korb* (glosa mía ambigua, no cuenta como spot).
