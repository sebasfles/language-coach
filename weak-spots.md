# weak-spots — the churn table

> A single small table tracking error churn, session-indexed. Maintained by `/close-day`; read by `/lesson` (the `00-check` retrieval warm-up is ordered most-churned first).
>
> - **category** = the error TYPE (short tag), so errors are queryable per-type over time. For German use tags such as: `gender` (der/die/das), `case` (Nom/Akk/Dat/Gen), `word-order` (V2 / verb-final / TeKaMoLo), `tense/aspect`, `agreement` (adjective endings / subject-verb), `preposition`, `verb-form` (irregular / auxiliary / personal endings), `separable-prefix`, `false-friend`, `spelling`, `word-choice`, `register`.
> - **status** = `active` / `watch` / `cleared`. A spot clears only after ≥2 spaced correct reappearances (active → watch → cleared); a re-failure flips it back to `active` and increments `times_recurred`. **Exception — `gender` (lexical der/die/das):** long-haul exposure item, not clear-and-done (see `[[gender-is-long-haul-exposure]]`); recirculate gently, don't penalize.
> - `/close-day` assigns the category when it adds a new spot (inferred from the `/grade` error pattern) and may refine it on churn.

| spot | source | category | first_seen_session | last_seen_session | times_recurred | status | cleared_session |
|---|---|---|---|---|---|---|---|
| 🔴 **`fahren`: Umlaut en 3.ª persona** (*er **fährt***, no *fahrt*) — **el nº1 ahora** | 03-reading s11 · 00-check s12 · **s13: 00-check ✓ PERO 03-writing *fahrt*×2 + *Farht*** | verb-form | 11 | 13 | 2 | active |  |
| 🔴 **verbos separables — NO partir en frase principal** (*Ich zurückkomme* → *komme … zurück*) · participio ✅ resuelto | s11 · s12 (participio ✗✗) · **s13: 00-check participios ✓✓ PERO 03-writing *Ich zurückkomme* ✗** | separable-prefix | 11 | 13 | 2 | active |  |
| 🆕 **modal + PARTICIPIO en vez de infinitivo** (*können … gesehen* → *sehen*) — mezcla las dos Satzklammern | **03-writing s13** | verb-form | 13 | 13 | 0 | active |  |
| 🆕 **ortografía bajo velocidad**: transposición (*hr↔rh*, *ie↔ei*), diéresis omitida (*mochte*→möchte), mayúsculas | **s13: 8+ casos** (*nein, zug, uhr, zwöelf, färsht, abfärhst, seiben, fünfzhen, mochte×2, FahrKarte, problem*) | spelling | 13 | 13 | 0 | active |  |
| **-en de más** (–n/–en fuera de masc-Akk) — 🔁 **RE-ACTIVADO** | s9 · s10 · 00-check s11 (*Zügen*) · s12 LIMPIO → watch · **s13: *einen Restaurant* (neutro) ✗** | case | 9 | 13 | 3 | active |  |
| **género léxico** (der/die/das) — **EXPOSICIÓN de largo plazo, no penalizar** | 00-check s3–s12 · **s13: *Welcher Restaurant*→welches, *einen Restaurant*** | gender | 3 | 13 | 2 | active |  |
| **`groß` (adj) vs `Größe`** (talla) | 03-writing s10 (*mit große* ×2) — sin probar desde entonces | word-choice | 10 | 10 | 0 | active |  |
| **pronombre en imperativo con `Sie`** (*Helfen Sie mir*) | 02-grammar s10 — sin probar desde entonces | word-order | 10 | 10 | 0 | active |  |
| ✅ **V2 tras elemento frontal** — **gran mejora**: 5 contextos limpios en s13 | s12 (3 fallos) · **s13: 00-check 4/4 ✓ · drill 12/12 ✓ · traducción 3/3 ✓ · escritura 2/2 ✓** *(el aparente fallo de t02 era **Linksversetzung**, verificada como estándar → NO era fallo de V2)* | word-order | 12 | 13 | 0 | watch |  |
| **`haben` conjugación por persona** (ich **habe** / du hast / er hat) | s10 · s11 (*Habst*) · s12 (*ich hat* ×3) · **s13 LIMPIO** (00-check ✓✓, sin fallos en escritura) | verb-form | 10 | 13 | 2 | watch |  |
| **kaufen vs zahlen** | s8 · cleared@10 · s12 recaída · **s13 LIMPIO** (00-check ✓✓ + *zahlen* ✓ en escritura) | word-choice | 8 | 13 | 1 | watch |  |
| 🆕 **`wann` (pregunta) vs `wenn` (condición)** | **s13: ej-02 *wenn* por *wann* ✗ · PERO 03-writing *Wann fährt…* ✓ y *wenn du…* ✓ en el mismo texto** | word-choice | 13 | 13 | 0 | watch |  |
| **definido/indefinido + Akk masc** (*der Saft*→*den*) | s7 · s8✓,s9✗,s10✓ · s11 (1 desliz) · s12 LIMPIO · **s13: *einen Termin* ✓** | word-choice | 7 | 13 | 1 | watch |  |
| **registro du/Sie** (mezcla en contexto formal) | **03-writing s13 t01** (ventanilla: *du* + *Zahlen Sie*) — t02 consistente ✓ | register | 13 | 13 | 0 | watch |  |
| concordancia de *du* en **pregunta invertida** (*Kannst du*) | s8 · s9✗, s10✓ — sin probar desde entonces | verb-form | 8 | 10 | 1 | watch |  |
| **concordancia con plurales** | 03-writing s9 · 00-check s10✓ — sin probar desde entonces | agreement | 9 | 10 | 0 | watch |  |
| **`sein`: `ihr` → seid** | s1 · cleared@3 · s10 recaída · s11 ✓ · s12 ✓ | verb-form | 1 | 12 | 1 | cleared | 12 |
| **`kein-`/`ein-` femenino → keine** | s6 · cleared@9 · s10 recaída · s11 ✓ · s12 ✓ · **s13 ✓✓** (*keine Zeit*, *kein Problem*) | case | 6 | 13 | 1 | cleared | 12 |
| posición de **nicht** | s6 · s7,s8 · **s12 ✓✓✓** | word-order | 6 | 12 | 0 | cleared | 8 |
| `and` → `und` | 03-writing s6 · s7 | false-friend | 6 | 7 | 0 | cleared | 7 |
| mayúscula de sustantivos *(≠ el spot nuevo de ortografía: aquello era desconocimiento, esto es velocidad)* | 02-grammar s3 · 00-check s5,s6 | spelling | 3 | 6 | 1 | cleared | 6 |
| formas exactas de plural: *Studenten* | 02-grammar s3 · 00-check s4,s5,s6 | word-form | 3 | 6 | 1 | cleared | 6 |
| terminación verbal según la persona (*fährt/bezahle*) | 02-grammar s4 · 00-check s5,s6 | verb-form | 4 | 6 | 0 | cleared | 6 |
| número + concordancia: *Meine Muttersprache ist* | 03-writing s2 · 00-check s3,s4 | agreement | 2 | 4 | 1 | cleared | 4 |
| `die Stadt` vs `das Land` | 02-grammar s2 · 00-check s3,s4 | word-choice | 2 | 4 | 1 | cleared | 4 |
| `ist` vs inglés *is* | 02-grammar s2 · 00-check s3,s4 | verb-form | 2 | 4 | 1 | cleared | 4 |

> **Churn de la sesión 13:**
> - 🎉 **V2 → `watch`** tras 5 contextos limpios (check 4/4, drill 12/12, traducción 3/3, escritura **2/2**). **RECTIFICACIÓN importante:** el aparente fallo de la tarea 02 (*Das letzte Mal wir haben uns gesehen*) **NO era un fallo de V2** — era una **Linksversetzung** (dislocación a la izquierda con retomador *das*), **verificada como construcción estándar** en Grammis/IDS y la Variantengrammatik; en ella el bloque desplazado queda **fuera del recuento de V2**. El learner lo argumentó él mismo y tenía razón. El hueco real es **el subordinante `als` + verbo final** — material A2/B1 **no enseñado**.
> - ✅ **Tres → `watch`:** **`haben` por persona** (sesión limpia tras 3 fallos en s12), **kaufen/zahlen** (limpio tras la recaída), y el V2.
> - 🔴 **`fahren` Umlaut es ahora el nº1**: correcto en el check pero **3 fallos en escritura** (*fahrt*×2, *Farht*). tr→2. Patrón clarísimo de **reconocimiento ✅ / producción ⏳**.
> - 🔴 **Separables**: el **participio** ya está resuelto (00-check ✓✓), pero reaparece **no partir en frase principal** (*Ich zurückkomme*). tr→2, descripción refinada.
> - 🔁🔻 **`-en de más` RE-ACTIVADO** desde `watch`: *einen Restaurant* (neutro). tr→3.
> - 🆕 **modal + participio** (*können … gesehen*): confusión entre las dos Satzklammern **justo porque ahora domina las dos por separado**. Muy productivo → `active`.
> - 🆕 **ortografía bajo velocidad**: **8+ casos hoy**, todos en palabras que demuestra conocer en el mismo folio. NO es el viejo spot de mayúsculas (aquel era desconocimiento). Acción concreta: **1 minuto de relectura antes de entregar** — relevante para el examen de la s14.
> - 🆕 **`wann`/`wenn`** → `watch`: falló en el ej-02 pero **usó las dos correctamente** en la escritura posterior.
> - 🆕 **registro du/Sie** → `watch` (1 caso, en ventanilla).
> - 🌱 **Reaches A2/B1 exitosos** (no son weak-spots, son señal para `/recalibrate`): **damit** (adverbio pronominal, B1) ✓ · **uns sehen** (recíproco, A2) ✓✓ · **früher als** (comparativo, A2) ✓ · **Linksversetzung** (lógica correcta, solo faltaba *als*). **Está empujando hacia A2/B1 por su cuenta; lo que le falta son preposiciones con caso y subordinación.**
> - **Nota:** *halb* solo funciona con **1–12** (*halb fünfzehn* ✗) → matiz añadido a `zahlen-uhrzeit`, no spot aparte.
