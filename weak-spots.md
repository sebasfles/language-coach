# weak-spots — the churn table

> A single small table tracking error churn, session-indexed. Maintained by `/close-day`; read by `/lesson` (the `00-check` retrieval warm-up is ordered most-churned first).
>
> - **category** = the error TYPE (short tag), so errors are queryable per-type over time. For German use tags such as: `gender` (der/die/das), `case` (Nom/Akk/Dat/Gen), `word-order` (V2 / verb-final / TeKaMoLo), `tense/aspect`, `agreement` (adjective endings / subject-verb), `preposition`, `verb-form` (irregular / auxiliary / personal endings), `separable-prefix`, `false-friend`, `spelling`, `word-choice`, `valency`, `register`.
> - **status** = `active` / `watch` / `cleared`. A spot clears only after ≥2 spaced correct reappearances (active → watch → cleared); a re-failure flips it back to `active` and increments `times_recurred`. **Exception — `gender` (lexical der/die/das):** long-haul exposure item, not clear-and-done (see `[[gender-is-long-haul-exposure]]`); recirculate gently, don't penalize.
> - `/close-day` assigns the category when it adds a new spot (inferred from the `/grade` error pattern) and may refine it on churn.
> - ⚠️ **Nothing that is NOT YET TAUGHT belongs in this table.** Preposition-with-case, Dativ, TeKaMoLo and adjective endings are **readiness signals**, not failures — they live in `STATE.md`, not here.

| spot | source | category | first_seen_session | last_seen_session | times_recurred | status | cleared_session |
|---|---|---|---|---|---|---|---|
| 🔴 **auxiliar `sein` con verbos de movimiento — SOLO en escritura libre** (*hat abgefahren* → **ist**) | **s14 examen: ejercicios 3/3 ✓ (*bin geblieben, bin gefahren, bin aufgestanden*) PERO *hat abgefahren* ✗ en la Aufgabe 1** | tense/aspect | 14 | 14 | 0 | active |  |
| 🔴 **cambio vocálico e→i / e→ie no se activa** (*Sehst* → **siehst**, *nehme* → **nimmt**) | **s14: ítem 19 *Sehst* ✗ y lectura #5 *nehme* ✗ — PERO produjo *empfiehlst* ✓ en escritura libre** | verb-form | 14 | 14 | 0 | active |  |
| 🆕🔴 **valencia verbal: transitivo sin objeto acusativo** (*Wo empfiehlst du?* → *empfehlen* exige objeto) | **s14 Aufgabe 1.** ⚠️ Categoría nueva. **Sustituye** la etiqueta falsa «confusión de W-Fragen» de la corrección v1 | valency | 14 | 14 | 0 | active |  |
| 🟠 **participios fuertes regularizados** (*gelauft* → **gelaufen**) | **s14 Aufgabe 2** | verb-form | 14 | 14 | 0 | active |  |
| 🟠 **concordancia `Sie`/`sie` + verbo** (*möchte Sie* → *möchten Sie* / *möchte sie*) | **s14 ítem 29** — enlaza con el spot de registro du/Sie en `watch` | agreement | 14 | 14 | 0 | active |  |
| **ortografía bajo velocidad**: transposición de letras, diéresis omitida, vocales cambiadas | s13: **8+ casos** (*nein, zug, zwöelf, färsht, mochte×2, FahrKarte…*) · **s14: MEJORA CLARA — 1 caso real puntuable** (*halb **nein*** → neun) **+ 1 en zona sin puntuar** (*is* → ist) | spelling | 13 | 14 | 1 | active |  |
| **género léxico** (der/die/das) — **EXPOSICIÓN de largo plazo, NO penalizar** | 00-check s3–s12 · s13 (*Welcher Restaurant*) · **s14: *die Fahrrad* ✗ (es *das*) — pero *eine Fahrkarte* ✓ y *ein Brot* ✓** | gender | 3 | 14 | 3 | active |  |
| **`groß` (adj) vs `Größe`** (talla) | 03-writing s10 (*mit große* ×2) — sin probar desde entonces | word-choice | 10 | 10 | 0 | active |  |
| **pronombre en imperativo con `Sie`** (*Helfen Sie mir*) | 02-grammar s10 — sin probar desde entonces | word-order | 10 | 10 | 0 | active |  |
| 🎉 **`fahren`: Umlaut en 3.ª persona** — **era el nº1; LIMPIO en todo el examen** | s11 · s12 · s13 (3 fallos en escritura) · **s14: *fährt* ✓✓✓✓** (2.1 #8 · 2.2 #17 · 2.5 #38 · Fehlersuche #31) | verb-form | 11 | 14 | 2 | watch |  |
| 🎉 **verbos separables — partir en frase principal** — **LIMPIO en el examen** | s11 · s12 · s13 (*Ich zurückkomme* ✗) · **s14: *fährt…ab* ✓, *stehst…auf* ✓, *Kommt…an?* ✓, *komme…zurück* ✓** | separable-prefix | 11 | 14 | 2 | watch |  |
| 🎉 **modal + INFINITIVO (no participio)** — **LIMPIO en el examen** | s13 (*können … gesehen* ✗) · **s14: *fahren* ✓, *können…gehen* ✓, *trinken* ✓, *können uns sehen* ✓** | verb-form | 13 | 14 | 0 | watch |  |
| 🎉 **`-en` de más** (–n/–en fuera de masc-Akk) — **LIMPIO en el examen** | s9 · s10 · s11 (*Zügen*) · s12 limpio · s13 (*einen Restaurant* ✗) · **s14: *einen Termin* ✓ (masc Akk correcto) + *eine/ein* con género correcto ✓✓** | case | 9 | 14 | 3 | watch |  |
| 🆕 **`kein`/`nicht` con sustantivo sin determinante** (*essen nicht gekauft* → **kein Essen**) | **s14 Aufgabe 2** — contrapeso fuerte: *keine Fahrkarte* ✓, *keine Zeit* ✓, *kein Problem* ✓ en el mismo examen | word-choice | 14 | 14 | 0 | watch |  |
| **V2 tras elemento frontal** | s12 (3 fallos) · s13 (5 contextos limpios) · **s14: limpio en TODO el examen** (*In Bremen ist er* · *mit Karte kann man* · *Gestern habe ich* · *Am Samstag habe ich* · *Um acht Uhr hat* · *Täglich lese ich*) | word-order | 12 | 14 | 0 | watch |  |
| **`haben` conjugación por persona** | s10 · s11 (*Habst*) · s12 (*ich hat* ×3) · s13 limpio · **s14 limpio** (*habe* ✓✓) | verb-form | 10 | 14 | 2 | watch |  |
| **kaufen vs zahlen** | s8 · cleared@10 · s12 recaída · s13 limpio · **s14: *gekauft* ✓ ×3, *zahlen* ✓** | word-choice | 8 | 14 | 1 | watch |  |
| **`wann` (pregunta) vs `wenn` (condición)** | s13 (1 fallo, 2 aciertos el mismo día) · **s14: *Wann fährt dein Zug ab?* ✓** | word-choice | 13 | 14 | 0 | watch |  |
| **definido/indefinido + Akk masc** (*der Saft*→*den*) | s7 · s8–s12 vaivén · s13 (*einen Termin* ✓) · **s14: *einen Termin* ✓, *den Bus* ✓** | word-choice | 7 | 14 | 1 | watch |  |
| **registro du/Sie** (mezcla en contexto formal) | 03-writing s13 t01 — **s14: no probado en producción libre** (pero ver la concordancia *Sie/sie* arriba) | register | 13 | 13 | 0 | watch |  |
| concordancia de *du* en **pregunta invertida** (*Kannst du*) | s8 · s9✗, s10✓ — sin probar desde entonces | verb-form | 8 | 10 | 1 | watch |  |
| **concordancia con plurales** | 03-writing s9 · 00-check s10✓ — sin probar desde entonces | agreement | 9 | 10 | 0 | watch |  |
| **`sein`: `ihr` → seid** | s1 · cleared@3 · s10 recaída · s11 ✓ · s12 ✓ | verb-form | 1 | 12 | 1 | cleared | 12 |
| **`kein-`/`ein-` femenino → keine** | s6 · cleared@9 · s10 recaída · s11 ✓ · s12 ✓ · s13 ✓✓ · **s14 ✓✓** (*keine Fahrkarte*, *keine Zeit*) | case | 6 | 14 | 1 | cleared | 12 |
| posición de **nicht** | s6 · s7,s8 · s12 ✓✓✓ · **s14: *keine Fahrkarte gekauft* ✓** | word-order | 6 | 14 | 0 | cleared | 8 |
| `and` → `und` | 03-writing s6 · s7 | false-friend | 6 | 7 | 0 | cleared | 7 |
| mayúscula de sustantivos | 02-grammar s3 · 00-check s5,s6 *(⚠️ el *essen* de la s14 es confusión verbo/sustantivo, no fallo de la regla — ver el spot de kein/nicht)* | spelling | 3 | 6 | 1 | cleared | 6 |
| formas exactas de plural: *Studenten* | 02-grammar s3 · 00-check s4,s5,s6 | word-form | 3 | 6 | 1 | cleared | 6 |
| terminación verbal según la persona | 02-grammar s4 · 00-check s5,s6 | verb-form | 4 | 6 | 0 | cleared | 6 |
| número + concordancia: *Meine Muttersprache ist* | 03-writing s2 · 00-check s3,s4 | agreement | 2 | 4 | 1 | cleared | 4 |
| `die Stadt` vs `das Land` | 02-grammar s2 · 00-check s3,s4 | word-choice | 2 | 4 | 1 | cleared | 4 |
| `ist` vs inglés *is* | 02-grammar s2 · 00-check s3,s4 · **s14: NO se reactiva.** El *is* del ítem 46 fue en la **zona sin puntuar** y es un **typo bajo velocidad** (pertenece a la fila `spelling`), **no** una confusión inglés↔alemán — que es lo que este spot mide. En el mismo examen escribió *ist* correctamente varias veces | verb-form | 2 | 4 | 1 | cleared | 4 |

> **Churn de la sesión 14 (el examen de 90 min):**
>
> **🎉 CINCO spots pasan a `watch` — la mejor cosecha del programa.** El examen probó los cinco y **los cinco salieron limpios**: **`fahren` Umlaut** (era el nº1; *fährt* ✓ cuatro veces), **separables partidos** (cuatro contextos), **modal + infinitivo** (cuatro contextos), **`-en` de más** (*einen Termin* ✓ + los dos indefinidos con género correcto) y **V2** (seis contextos, incluido *Täglich lese ich*).
>
> **🔴 Cinco spots nuevos, y todos apuntan a lo mismo.** *hat abgefahren* · *Sehst* · *gelauft* · *möchte Sie* · valencia verbal. El patrón es **automatización, no conocimiento**, y hay dos pruebas cruzadas que lo demuestran:
> | | |
> |---|---|
> | Auxiliar `sein` en ejercicios | **3/3 ✓** |
> | El mismo auxiliar escribiendo libre | ❌ *hat abgefahren* |
> | e→ie en *empfehlen* (escritura libre) | ✅ *empfiehlst* |
> | e→ie en *sehen* (ejercicio) | ❌ *Sehst* |
>
> Y el dato que lo cierra: **Fehlersuche 6/6** — los seis ítems eran calcos exactos de sus seis weak-spots activos y **los cazó todos**. Sabe las reglas; no se le activan mientras piensa en el contenido. **Prescripción: más reps de producción al mismo nivel, nunca material más fácil.**
>
> **🆕 Categoría nueva: `valency`.** *Wo empfiehlst du?* no era confusión *wo/was* (ese diagnóstico de la corrección v1 era **falso** — el learner lo apeló y tenía razón). Es que *empfehlen* exige objeto acusativo. Prueba limpia: *«Wo können wir essen?»* es perfecto, porque *essen* no lo exige.
>
> **📉 La ortografía mejoró mucho:** de 8+ casos en la s13 a **2 reales** en la s14. Se mantiene `active` pero con el aviso reducido — dos de los cuatro ejemplos que cité en la corrección v1 **no existían**.
>
> **⚠️ Lo que NO entra en esta tabla, a propósito:** *nach/zu/in*, Dativo, TeKaMoLo, terminaciones de adjetivo y el caso de *der U-Bahn*. **No son fallos suyos: es material no enseñado**, y la constitución (§2) prohíbe exigirlo en producción. Son **señal de readiness** y viven en `STATE.md`. En la Aufgabe 2 del examen **no existía ninguna forma correcta** de decir «fui al supermercado» con A1 #1–#18 — eso fue fallo de diseño de la tarea.
>
> **🌱 Reaches A2/B1 exitosos (señal para el roadmap, no weak-spots):** *mit dem Bus* (Dativo) · *billiger als* (comparativo) · `denn` resolviendo un ítem que pedía *weil* · omisión de `dass` con V2 · *uns sehen* · *damit* · *im Restaurant* · **`war` ×2** (el Präteritum nativo de *sein*) · **`empfiehlst`** (e→ie en un verbo visto solo como participio). **Siete estructuras sin enseñar, correctas.**
>
> **📋 Fuera de la tabla pero anotado en `STATE.md`:** **cumplimiento de requisitos de tarea** — se dejó **dos de seis** en la Aufgabe 2 (ningún modal, solo dos horas). No es un error de lengua y no se puede drillar en un 00-check; se ataja con **checklist marcable** en cada tarea de escritura.
