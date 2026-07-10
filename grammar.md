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
| Präsens: `sein` + Personalpronomen + V2 + W-Fragen (`praesens-sein-personalpronomen`) | introduced@1 practicing@1 mastered@3 | 95% s1; recycle 85% s2; s3 sein 4/4 + V2 correcto + `ihr seid` **cleared** → fiable a lo largo de 3 sesiones. Ref: `grammar/praesens-sein-personalpronomen.md` |
| Artikel & Genus im Nominativ: der/die/das + ein/eine (`artikel-genus-nominativ`) | introduced@2 practicing@2 | s5 00-check 100%, pero s6 falla en producción (*die Käse*, *Das Suppe*). El **género léxico** se trata ahora como **exposición de largo plazo** (no clear-and-done; ver weak-spot `gender` y `[[gender-is-long-haul-exposure]]`). Sigue **practicing** (recircular suave). Ref: `grammar/artikel-genus-nominativ.md` |
| Plural der Nomen (Nominativ): `die` para todo plural + 5 patrones (`plural-der-nomen`) | introduced@3 practicing@3 mastered@6 | s3 89%/88% → s4/s5/s6 formas exactas correctas (*Studenten/Schwestern/Zahlen*); weak-spot `word-form` **cleared s6** → fiable. Ref: `grammar/plural-der-nomen.md` |
| Präsens: Verben mit Vokalwechsel (e→i, e→ie, a→ä) + `haben` (`praesens-vokalwechsel-haben`) | introduced@4 practicing@4 mastered@6 | s4 100%/93% → s5/s6 *fährt/bezahle/isst* correctos; weak-spot `verb-form` (terminación) **cleared s6** → fiable. Ref: `grammar/praesens-vokalwechsel-haben.md` |
| Akkusativ: der→den / ein→einen + pronombres (mich/dich/ihn…) (`akkusativ`) | introduced@5 practicing@5 mastered@7 | s5 100%/100%; s7 test: *einen Kaffee/eine Suppe/einen Käse* correctos → fiable. (El desliz definido/indefinido del test es `word-choice`, no de caso.) Ref: `grammar/akkusativ.md` |
| Negation: `kein` (declina como ein-) vs `nicht` (`negation-kein-nicht`) | introduced@6 practicing@6 | s6 83%/90%; s7 test kein/keinen/nicht correctos. Lógica dominada; pendiente el **femenino *keine*** (sin probar limpio) + posición de *nicht* (watch). Sigue **practicing**. Ref: `grammar/negation-kein-nicht.md` |
| Koordinierende Konjunktionen: und/oder/aber/denn/sondern (`koordinierende-konjunktionen`) | introduced@7 practicing@7 | s7: ej **100%** (incl. aber vs sondern, denn). No cambian el orden. Recién introducido → **practicing**. Ref: `grammar/koordinierende-konjunktionen.md` |
| Modalverben: können/müssen/wollen/dürfen/sollen/mögen (+möchten) + Satzklammer (`modalverben`) | introduced@8 practicing@8 | s8: ej-01 **100%** (conjugar, ich=er sin -t) / ej-02 **90%** (Satzklammer) / ej-03 **88%**. Satzklammer sólida; pendiente *du* en pregunta invertida (*Kannst du*) y léxico kaufen/zahlen. **practicing**. Ref: `grammar/modalverben.md` |

> `/close-day` adds and advances rows here. Topics stay `practicing` while still error-prone or not yet automatic — recycle, don't check off.
