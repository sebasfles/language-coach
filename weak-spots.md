# weak-spots — the churn table

> A single small table tracking error churn, session-indexed. Maintained by `/close-day`; read by `/lesson` (the `00-check` retrieval warm-up is ordered most-churned first).
>
> - **category** = the error TYPE (short tag), so errors are queryable per-type over time. For German use tags such as: `gender` (der/die/das), `case` (Nom/Akk/Dat/Gen), `word-order` (V2 / verb-final / TeKaMoLo), `tense/aspect`, `agreement` (adjective endings / subject-verb), `preposition`, `verb-form` (irregular / auxiliary / personal endings), `separable-prefix`, `false-friend`, `spelling`, `word-choice`, `register`.
> - **status** = `active` / `watch` / `cleared`. A spot clears only after ≥2 spaced correct reappearances (active → watch → cleared); a re-failure flips it back to `active` and increments `times_recurred`. **Exception — `gender` (lexical der/die/das):** long-haul exposure item, not clear-and-done (see `[[gender-is-long-haul-exposure]]`); recirculate gently, don't penalize.
> - `/close-day` assigns the category when it adds a new spot (inferred from the `/grade` error pattern) and may refine it on churn.

| spot | source | category | first_seen_session | last_seen_session | times_recurred | status | cleared_session |
|---|---|---|---|---|---|---|---|
| **`haben` conjugación por persona** (**ich habe** / du hast / er hat) — s12: ***ich hat* ×3** | 03-writing s10 · 00-check s11 (*Habst*) · **00-check s12 (*Hast* ✓) vs 03-writing s12 (*ich hat* ×2 + s12 t01 *und hat*)** | verb-form | 10 | 12 | 2 | active |  |
| 🆕 **V2 tras elemento frontal** (si algo ocupa la pos. 1, el verbo va 2.º) — *Am Abend**, ich bin*** · *Endlich**, ich habe*** · *dann **ich bin*** | **03-writing s12 (3 casos; PERO *Gestern bin ich* ✓)** | word-order | 12 | 12 | 0 | active |  |
| **género léxico** (der/die/das) — **EXPOSICIÓN de largo plazo, no penalizar**; s12 también en **pronombre** (*Es* por *Er* = der Zug) y *an der Restaurant* (das) | 00-check s3–s11 · 02-grammar · **03-writing s12** | gender | 3 | 12 | 2 | active |  |
| **verbos separables** — **partición ✅ resuelta (s12)**; pendiente **conservar prefijo + `-ge-` en el Partizip II** | 02-grammar s11 · 03-writing s11 · **s12: 00-check partición ✓✓ · ej-02 *gekommen*/*umstiegen* ✗✗ · 03-writing *angekommen*/*zurückgekommen* ✓✓✓** | separable-prefix | 11 | 12 | 1 | active |  |
| 🆕 **`fahren`: Umlaut en 3.ª persona** (*er **fährt***, no *fahrt* — *fahrt* es de *ihr*) | 03-reading s11 (*er fahrt*) · **00-check s12 (*fahrt*)** | verb-form | 11 | 12 | 1 | active |  |
| 🔁🔻 **léxico comprar (kaufen) vs pagar (zahlen)** — **RECAÍDA** (estaba cleared@10) | 02-grammar s8 · 00-check s9✓ · 03-writing s10✓ (cleared@10) · **02-grammar s12 (*bezahlt* por *gekauft*, ej-03 #8)** | word-choice | 8 | 12 | 1 | active |  |
| **`groß` (adj) vs `Größe`** (talla, sustantivo) | 03-writing s10 (*mit große* ×2) | word-choice | 10 | 10 | 0 | active |  |
| **pronombre en imperativo con `Sie`** (*Helfen Sie mir*; + omisión de *mir*) | 02-grammar s10 (ej-02/ej-03) | word-order | 10 | 10 | 0 | active |  |
| **-en de más** (añadir -n/-en fuera de masc-Akk) | 02-grammar s9 · 03-writing s9,s10 · 00-check s11 (*Zügen*) · **s12 LIMPIO** (*eine Fahrkarte*, *einen Kaffee*, *meine Karte*, *den Bus* ✓) | case | 9 | 12 | 2 | watch |  |
| **definido/indefinido + Akk masc** (*der Saft*→*den*) | 05-test s7 · 00-check s8✓,s9✗,s10✓ · s11 (1 desliz *dieser*) · **s12 LIMPIO** (*den Bus*, *auf den Zug*, *einen Kaffee* ✓) | word-choice | 7 | 12 | 1 | watch |  |
| concordancia de *du* en **pregunta invertida** (*Kannst du*) | 02-grammar s8 · 00-check s9✗,s10✓ | verb-form | 8 | 10 | 1 | watch |  |
| **concordancia con plurales** (*Schuhe* → sin *eine*; verbo plural) | 03-writing s9 · 00-check s10✓ | agreement | 9 | 10 | 0 | watch |  |
| **`sein`: `ihr` → seid** | 00-check s2,s3 (cleared@3) · s10 (*Seind* ✗) · escalación s11 ✓ · **00-check s12 (*Seid ihr müde?* ✓)** | verb-form | 1 | 12 | 1 | cleared | 12 |
| **`kein-`/`ein-` femenino → keine** | 02-grammar s6 · cleared@9 · s10 (*kein Hose* ✗) · 00-check s11 ✓ · **00-check s12 (*keine Zeit* ✓)** | case | 6 | 12 | 1 | cleared | 12 |
| posición de **nicht** | 03-writing s6 · 00-check s7,s8 · **s12 ✓✓✓** (*nicht gekauft*, *nicht gehabt*, *nicht zu Fuß*) | word-order | 6 | 12 | 0 | cleared | 8 |
| `and` → `und` | 03-writing s6 · 00-check/02-grammar s7 | false-friend | 6 | 7 | 0 | cleared | 7 |
| mayúscula de sustantivos | 02-grammar s3 · 00-check s5,s6 | spelling | 3 | 6 | 1 | cleared | 6 |
| formas exactas de plural: *Studenten* | 02-grammar s3 · 00-check s4,s5,s6 | word-form | 3 | 6 | 1 | cleared | 6 |
| terminación verbal según la persona (*fährt/bezahle*) | 02-grammar s4 · 00-check s5,s6 | verb-form | 4 | 6 | 0 | cleared | 6 |
| número + concordancia: *Meine Muttersprache ist* | 03-writing s2 · 00-check s3,s4 | agreement | 2 | 4 | 1 | cleared | 4 |
| `die Stadt` vs `das Land` | 02-grammar s2 · 00-check s3,s4 | word-choice | 2 | 4 | 1 | cleared | 4 |
| `ist` vs inglés *is* | 02-grammar s2 · 00-check s3,s4 | verb-form | 2 | 4 | 1 | cleared | 4 |

> **Churn de la sesión 12:**
> - 🎉🎉 **DOS CLEARED**: **`sein: ihr → seid`** (recaída en s10 → limpio en s11 y s12) y **`kein-`/`ein-` femenino** (recaída en s10 → limpio en s11 y s12). Ambos **cerrados@12**.
> - 🆕🔴 **V2 tras elemento frontal** — el weak-spot más importante de hoy: 3 casos en escritura (*Am Abend, ich bin* · *Endlich, ich habe* · *dann ich bin*), **con acierto intercalado** (*Gestern bin ich* ✓). Diagnóstico: generaliza la regla de las conjunciones (*aber/denn* NO invierten) a los adverbios (*dann/deshalb* SÍ invierten) + coma a la española. `word-order`.
> - 🔴 **`haben` por persona → recurre fuerte:** *Hast du* ✓ en el check, pero ***ich hat* ×3** en producción libre. El learner lo identificó él mismo como automatismo de Anki. tr→2.
> - 🔁🔻 **`kaufen` vs `zahlen` — RECAÍDA** (cleared@10): *bezahlt* por *gekauft*. Dirección invertida respecto a antes. → `active`, tr→1.
> - 🟰 **Separables — media victoria:** la **partición está resuelta** (00-check ✓✓, y *Steige…aus* desde s11); ahora falla en el **participio** (ej-02 *gekommen*/*umstiegen*) aunque en escritura salió bien 3 veces (*angekommen* ×2, *zurückgekommen*). Sigue `active` con la descripción refinada.
> - 🆕 **`fahren` Umlaut 3.ª persona** (*fahrt*→*fährt*): 2.ª aparición (s11 lectura, s12 check) → weak-spot propio; ver democión de `praesens-vokalwechsel-haben` en `grammar.md`.
> - ✅ **Dos → `watch`:** **-en de más** (sesión limpia: *eine Fahrkarte, einen Kaffee, meine Karte*) y **der→den** (*den Bus, auf den Zug, einen Kaffee*). Una limpia más y cierran.
> - ✅ **posición de `nicht`** (cleared@8) **re-confirmada** 3 veces en s12 — sigue cerrada, sin recaída.
> - ✅ **`warten auf` + Akkusativo — RESUELTO en observación:** ✗ s11 (*auf dir*), ✗ s12 t01 (*auf mir*), **✓ s12 t02 (*auf den Zug*)**. No se abre como weak-spot fijo (es rección B1) pero queda anotado.
> - **Notas (no weak-spots fijos):** Satzklammer incompleta (olvidó el participio, 1 caso) · *gekaufen* (patrón fuerte aplicado a verbo débil, 1 caso) · auxiliar *sind* con *essen* (1 caso; ancla: **objeto directo → haben**) · typos con transposición **hr→rh** (*Farht/Farhkarte*) y *zürück*→*zurück*.
> - **PREPOSICIONES CON CASO (A2, no enseñadas): 10 errores entre las dos tareas** — *um Bremen, um die Straßen, zum Kreuzung, mit die Fahrraden, in Bahnhof ×2, an der Kasse (movimiento), zum meine Haus, durch zwanzig Minuten, an der Restaurant*. **NO son weak-spots** (material no enseñado) pero son **el techo productivo actual** y el learner las pide explícitamente → **señal fuerte para `/recalibrate` (s14)**: adelantar A1 #19 / A2 #4–#5.
