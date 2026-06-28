# vocab — ledger → Anki

`ledger.csv` is the single cumulative vocabulary register, **upstream** of Anki (one-directional: ledger → Anki, never back). Scheduling and review progress live **inside Anki**, not in the CSV, so re-importing only ever adds new cards and never erases progress.

## Columns

`headword,translation_es,ipa,example_de,session_tag`

- **headword** — the canonical German headword and the **dedup key** (stable first field).
  - **Nouns: always include the article AND record the plural** — e.g. `das Haus, die Häuser` · `die Frau, die Frauen` · `der Tisch, die Tische`. The article is **part of** the canonical form and is never stripped.
  - **Verbs: record the unpredictable forms** — irregular Präteritum + Partizip II + auxiliary — e.g. `gehen – ging – ist gegangen`. Mark **separable prefixes** with a pipe: `an|rufen`.
  - Dedup is **case-insensitive** on this field; the article is never stripped.
- **translation_es** — the Spanish gloss (the content language).
- **ipa** — optional; fill it in for the hard items (ch ich-Laut vs ach-Laut, ä/ö/ü, long vs short vowels, z = [ts], w = [v], v = [f], st-/sp- = [ʃt]/[ʃp], final devoicing, glottal stop). Leave blank otherwise.
- **example_de** — one short German example sentence using the headword.
- **session_tag** — the session that introduced the item (e.g. `session-001`), used for batch tagging in Anki.

## Anki import steps

1. **Save / export as UTF-8.** The CSV already is; if you edit it in another tool, keep the encoding UTF-8 (so umlauts and ß survive).
2. In Anki: **File → Import…** and pick `vocab/ledger.csv`.
3. **Type:** "Notes in Plain Text (.csv)". **Field separator:** Comma.
4. **Allow HTML in fields:** off. Map the columns in order: `headword` → Front, `translation_es` → Back, then `ipa`, `example_de`, `session_tag` into extra fields of your note type (or fold IPA/example onto the Front/Back as you prefer).
5. **Dedup on the first field (`headword`).** Set "Existing notes" to **Update** (or **Ignore**) so re-imports update/skip duplicates by the first field rather than creating doubles. The CSV is already deduped on this key before it reaches you.
6. **New cards/day** ≈ the per-session batch (~15–30, the shared per-session vocab cap). Tag each import batch by its `session_tag` so you can find or suspend a session's words later.

> The ledger is written by `/lesson` (and `/harvest` if used); both de-duplicate on the `headword` first field, case-insensitively, article never stripped.

## Pronunciation / audio

Written pronunciation already lives in the **`ipa`** column (filled for the hard items by `/lesson` / `/harvest`). For **audio**, set it up on the **Anki side** — the skills don't change; they already write clean German in `headword` and `example_de`, which is all the TTS needs to read.

**TTS — recommended (built-in, free, syncs everywhere, no add-on, no stored files):**
1. In your note type's card template (**Note Type → Cards…**), add a TTS field where you want the audio — e.g. `{{tts de_DE:headword}}` (and/or `{{tts de_DE:example_de}}` to hear the example sentence).
2. Install a **German voice** on the device:
   - **Windows** (Anki Desktop): Settings → Time & language → Speech → **Add voices** → German.
   - **AnkiDroid** (Android): install/enable a German voice in the system **text-to-speech** settings (e.g. Google TTS).
   - **AnkiMobile** (iOS): a German voice in iOS settings.

   Anki then reads the German aloud on every device and it syncs (the `{{tts}}` is just template text). TTS is robotic but fine as a per-word reference.

**Forvo — real native audio:** for a human pronunciation of a specific word, look it up free on **forvo.com**. (Auto-pulling Forvo into Anki needs an add-on + API key — more setup; the website is the easy path.)

**Real rhythm / prosody** comes best from the Easy German clips + shadowing (see the project `README.md`), not from TTS.
