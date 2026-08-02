# level-history — CEFR per `/recalibrate` run

> Append-only. One row per `/recalibrate` run (every 14th session): session `N`, estimated CEFR per skill, and what changed and why.
> The graded skills (reading / writing / grammar) are estimated from `progress/scores.csv`; **listening and speaking** are estimated from the `/close-day` self-reports captured in the recaps (they have no `scores.csv` rows).
> Written by `/recalibrate`. Indexed by session number `N` — no calendar dates. Target (north star): B2/C1.

## Convention

One row per run. CEFR estimate per skill, plus a short "what changed & why" (roadmap pace adjustments, pull-forward candidates, plateaus).

| session N | reading | listening | writing | speaking | grammar | what changed & why |
|---|---|---|---|---|---|---|
| **14** | **A2** ⬆️ | **A1** = | **A2** ⬆️ | **A1** = | **A1 completo → entrando en A2** | **Primer `/recalibrate`.** Examen de 90 min: reading 91 (A2, con texto B1 glosado dentro) · grammar 94 · writing 82. **Reading → A2**: cuarta sesión consecutiva ≥91% en tier A2, respondiendo en alemán con V2 correcto. **Writing → A2**: narra en pasado encadenado con conectores y mezcla de tiempos (descriptor A2 de «mensaje/nota simple»); los fallos que quedan son de automatización, no de conocimiento. **Listening y speaking se QUEDAN en A1** — el examen dio el dato honesto: **2/5 sin subtítulos** vs 4/5 con ellos, y del speaking no hay ninguna evidencia interaccional en 14 sesiones (solo lectura en voz alta + monólogo). **Roadmap re-paceado: A1 se completó en 14 sesiones, no en ~35** (2,5× por delante) → bandas movidas a A2 N≈15–45 · B1 N≈40–85 · B2 N≈80–120. **Apertura de A2 reordenada** por evidencia productiva: el techo real del learner son las preposiciones con caso (en la Aufgabe 2 del examen **no existía forma correcta** de expresar lo pedido con A1). Adelantados: prep. de caso (#4/#5) justo tras Dativ, **Präteritum de sein/haben/modales (#7)** y **comparativos (#9)** — ya los produce solo —, y **weil/dass (#11a)**. **Landing honesto revisado: B1 sólido, con B2 alcanzable en gramática/lectura** — pero listening/speaking siguen limitados por horas, no por temario. |
