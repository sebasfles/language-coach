# level-history — CEFR per `/recalibrate` run

> Append-only. One row per `/recalibrate` run (every 28th session): session `N`, estimated CEFR per skill, and what changed and why.
> The graded skills (reading / writing / grammar) are estimated from `progress/scores.csv`; **listening and speaking** are estimated from the `/close-day` self-reports captured in the recaps (they have no `scores.csv` rows).
> Written by `/recalibrate`. Indexed by session number `N` — no calendar dates. Target (north star): B2/C1.

## Convention

One row per run. CEFR estimate per skill, plus a short "what changed & why" (roadmap pace adjustments, pull-forward candidates, plateaus).

| session N | reading | listening | writing | speaking | grammar | what changed & why |
|---|---|---|---|---|---|---|

> Empty until the first `/recalibrate` run (after session 28).
