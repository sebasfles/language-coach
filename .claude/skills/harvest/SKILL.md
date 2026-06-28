---
name: harvest
description: >
  Bridge a reading or a listening clip to the vocabulary ledger: take the words the learner
  didn't know and append correctly formatted rows to vocab/ledger.csv, mirroring the same items
  into the session's class/01-vocab/new-words.md diff. Optional — its work can also be done inside
  /close-day. The learner flags the words; the skill does the formatting. Trigger on
  "harvest these words", "add these to my vocab", "I found new words in the reading or listening".
disable-model-invocation: true
---

# /harvest — reading / listening → vocab bridge

Append unknown words from a reading or a listening clip to the canonical `vocab/ledger.csv` (the Anki upstream) and record the same items in the current session's `lessons/session-NNN/class/01-vocab/new-words.md` (the human-readable diff), following the target-language vocabulary conventions in `CLAUDE.md`. Translations go in the **content language**; example sentences in the **target language**.

## Process
1. Take the words the learner flagged as unknown — from the reading or from the current session's `04-listening/` clip (optionally add a few level-appropriate ones they likely skipped).
2. **Respect the shared per-session cap.** The ~15–30 new items is a per-session **total** shared with `/lesson`, not a separate budget — harvest **tops up toward** the cap, it never stacks on top of it. Count what `/lesson` already introduced into `01-vocab/new-words.md` this session and add only up to the remaining room; route the cap through `LEARNING-PACE.md` (flex it down when the learner reports a large Anki review backlog). If the cap is already reached, add nothing and say so.
3. **Read the existing ledger header first**, then emit each row in the exact column order and count the header defines — including the optional **IPA** column if `vocab/ledger.csv` has one (leave it blank if you can't supply it; never shift the other fields). For each item produce: the headword in the conventional form (e.g., for gendered languages, with article + plural), a translation in the content language, and an example sentence in the target language. Tag with the current session (e.g., `session-NNN`).
4. **Dedupe on the canonical headword, the single source being the vocabulary/ledger convention in `CLAUDE.md`.** The stable first field is the canonical headword **with its article** for gendered languages (e.g., `das Haus`); the article is part of the canonical form and is **not** stripped. The dedup key is that first field compared **case-insensitively (lowercased)** — the same key `/lesson` uses. Append a row to `vocab/ledger.csv` only when its key is not already present.
5. Record the same items in `lessons/session-NNN/class/01-vocab/new-words.md` as a human-readable diff (create the file or the `01-vocab/` segment if it doesn't exist yet). This is the in-session view of what `vocab/ledger.csv` gained.

## Writes
- `vocab/ledger.csv` — the canonical cumulative vocabulary.
- `lessons/session-NNN/class/01-vocab/new-words.md` — the session's new-words diff.

## Note
This is the one piece deliberately kept optional. If you'd rather not run a separate step, fold this behavior into `/close-day` instead.
