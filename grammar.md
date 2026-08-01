# grammar — REGISTER of topics covered

> The register of which German grammar topics have been covered and their state.
> Read by `/lesson`; written by `/close-day`. Field names are English (scaffolding); topic names may appear in German.
> This is NOT the reference material — the explanations live in `grammar/<topic>.md`. This file only tracks state.

## Convention

Each topic carries one of three states, and **every state transition is stamped with the session number `N` it happened on**:

- **introduced@N** — first taught in session N.
- **practicing@N** — actively being drilled / recycled since session N (seen but still error-prone; must be recycled, not checked off).
- **mastered@N** — reliably correct since session N.

A topic is never a binary checkbox: a topic "seen" but still error-prone stays in `practicing`, not `mastered`. The transition sessions are load-bearing — `/lesson` uses the least-recently-touched non-active topic for the spaced grammar-recycle probe in `00-check`.

Record each transition the topic has reached, e.g. `introduced@3 practicing@5 mastered@12`.

## Topics

| topic | state(s) | notes |
|---|---|---|
| Präsens: `sein` + Personalpronomen + V2 + W-Fragen (`praesens-sein-personalpronomen`) | introduced@1 practicing@1 mastered@3 practicing@10 **mastered@12** | s10 demotado (*Seind*). **s11 escalación 10/10** + **s12 00-check *Seid ihr müde?* ✓** → weak-spot `ihr seid` **CLEARED@12** → **re-promovido a `mastered`**. ⚠️ Ojo: el **V2 en producción libre** es weak-spot aparte (3 fallos en s12) — ver `weak-spots.md`. Ref: `grammar/praesens-sein-personalpronomen.md` |
| Artikel & Genus im Nominativ: der/die/das + ein/eine (`artikel-genus-nominativ`) | introduced@2 practicing@2 | s5 00-check 100%, pero s6 falla en producción (*die Käse*, *Das Suppe*). El **género léxico** se trata ahora como **exposición de largo plazo** (no clear-and-done; ver weak-spot `gender` y `[[gender-is-long-haul-exposure]]`). Sigue **practicing** (recircular suave). Ref: `grammar/artikel-genus-nominativ.md` |
| Plural der Nomen (Nominativ): `die` para todo plural + 5 patrones (`plural-der-nomen`) | introduced@3 practicing@3 mastered@6 **practicing@11** | s3→mastered@6 (*Studenten/Schwestern/Zahlen* ✓). **s11: DEMOTADO** — el sondeo espaciado del 00-check falló: *die **Zügen*** por *die **Züge*** (añadió -n; nom. pl. no lleva -n, eso es Dativo pl.). Parece contaminación del `-en de más`. (*Linien* ✓.) **s12: *die Züge* ✓** — corregido; re-consolidando (sigue `practicing` hasta 2.ª limpia). Ref: `grammar/plural-der-nomen.md` |
| Präsens: Verben mit Vokalwechsel (e→i, e→ie, a→ä) + `haben` (`praesens-vokalwechsel-haben`) | introduced@4 practicing@4 mastered@6 **practicing@12** | s4–s6 fiable → mastered@6. **s12: DEMOTADO** por dos frentes: (a) **Umlaut 3.ª pers.** — *er **fahrt*** por *fährt* (s11 lectura + s12 check); (b) **`haben` por persona** — ***ich hat*** ×3 en escritura (aunque *Hast du* ✓ en el check). A recircular ambos. Ref: `grammar/praesens-vokalwechsel-haben.md` |
| Akkusativ: der→den / ein→einen + pronombres (mich/dich/ihn…) (`akkusativ`) | introduced@5 practicing@5 mastered@7 | s5 100%/100%; s7 test: *einen Kaffee/eine Suppe/einen Käse* correctos → fiable. (El desliz definido/indefinido del test es `word-choice`, no de caso.) Ref: `grammar/akkusativ.md` |
| Negation: `kein` (declina como ein-) vs `nicht` (`negation-kein-nicht`) | introduced@6 practicing@6 | s6 83%/90%; s7 test kein/keinen/nicht correctos. Lógica dominada; pendiente el **femenino *keine*** (sin probar limpio) + posición de *nicht* (watch). Sigue **practicing**. Ref: `grammar/negation-kein-nicht.md` |
| Koordinierende Konjunktionen: und/oder/aber/denn/sondern (`koordinierende-konjunktionen`) | introduced@7 practicing@7 **mastered@12** | s7 ej **100%**. **s12: sondeo espaciado 3/3** tras 5 sesiones sin tocarlo (*denn / aber / sondern* — incl. *sondern* tras negación) + *aber/und* correctos en escritura → **fiable**. Nota: aplica bien su regla de «no invierten»… y la **sobre-generaliza a los adverbios** → de ahí el weak-spot V2. Ref: `grammar/koordinierende-konjunktionen.md` |
| Modalverben: können/müssen/wollen/dürfen/sollen/mögen (+möchten) + Satzklammer (`modalverben`) | introduced@8 practicing@8 | s8: 100/90/88. Satzklammer sólida. **s11: desliz *du muss*→*musst*** (la forma de *du* del modal lleva -st) — nota, 1 caso; vigilar. **practicing**. Ref: `grammar/modalverben.md` |
| Possessivartikel: mein/dein/sein/ihr… (declinan como ein-/kein-) (`possessivartikel`) | introduced@9 practicing@9 | s9: 83/80/100. Mecánica y sein/ihr sólidos; **-en de más** fuera de masc-Akk = vaivén → weak-spot `case`. **practicing**. Ref: `grammar/possessivartikel.md` |
| Imperativ: du/ihr/Sie + `sei/seid/seien Sie` + separables (`imperativ`) | introduced@10 practicing@10 | s10: 100/92/67. Morfología sólida (e→i/ie sí, a→ä no, *Sei*, separables). **s11: imperativos correctos en escritura** (Geh/Warte/Steige…aus). Pendiente: **-e tras -t** y **separación del separable** (ver weak-spot `separable-prefix`). **practicing**. Ref: `grammar/imperativ.md` |
| dieser/welcher/jeder — der-words (Nom/Akk) (`dieser-welcher`) | introduced@11 practicing@11 | s11: ej-01 **100%** / ej-02 **70%** (el dip son verbos separables, NO el der-word). Concordancia de género sólida (*welcher/welche/welches*) y **masc Akk *diesen/welchen/jeden* correcto** (refuerza `der→den`). Desliz suelto: *dieser* por *diesen* (ej-02 #1). **practicing**. Ref: `grammar/dieser-welcher.md` |
| **das Perfekt**: `haben`/`sein` + Partizip II (Satzklammer) (`perfekt`) | **introduced@12 practicing@12** | s12 (roadmap A1 **#16+#17 juntos**): ej-01 **100%** (los 4 patrones del participio), ej-02 **80%** (**auxiliar 10/10**, participio 6/10), ej-03 **78%**. **Auxiliar haben/sein DOMINADO** (incl. *sein* con *sein*); lo pendiente es la **producción del participio** — 100% aislado pero se degrada al montar la frase (automatización). En lectura **distingue Perfekt de Präteritum** ✓. En escritura libre corrigió *angekommen*/*gekauft* que había fallado en el ejercicio. **practicing**. Ref: `grammar/perfekt.md` |

> `/close-day` adds and advances rows here. Topics stay `practicing` while still error-prone or not yet automatic — recycle, don't check off.
