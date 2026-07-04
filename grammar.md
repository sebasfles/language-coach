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
| Artikel & Genus im Nominativ: der/die/das + ein/eine (`artikel-genus-nominativ`) | introduced@2 practicing@2 | recycle en 00-check s4: *das Land*✓, *die Stadt*✓, pero *das Buch*✗(→der) y *das Essen*✗(→die). Género aún no automático → sigue **practicing** (ver weak-spot `gender`). Ref: `grammar/artikel-genus-nominativ.md` |
| Plural der Nomen (Nominativ): `die` para todo plural + 5 patrones (`plural-der-nomen`) | introduced@3 practicing@3 | s3: ej-01 89% / ej-02 88%. s4 00-check: *Schwestern*✓ *Zahlen*✓ (resueltos), *Studenten*✗ (n-Dekl., pendiente). Sigue **practicing**. Ref: `grammar/plural-der-nomen.md` |
| Präsens: Verben mit Vokalwechsel (e→i, e→ie, a→ä) + `haben` (`praesens-vokalwechsel-haben`) | introduced@4 practicing@4 | s4: ej-01 **100%** (conjugar) / ej-02 **93%** (producción). Dominó la regla "cambio solo du/er-sie-es" y los especiales (nimmt/isst). Leve desliz de terminación (*fähre→fährt*). Ref: `grammar/praesens-vokalwechsel-haben.md` |

> `/close-day` adds and advances rows here. Topics stay `practicing` while still error-prone or not yet automatic — recycle, don't check off.
