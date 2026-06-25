# Mind the Context — project memory

## What this is
A localization **Quality Pipeline** for the MAD 3 Hackathon (Solo Builder track, June 24–26).
Thesis: most QA tools check the translation in isolation. This one reads the **context** around
each string — the string ID, category, max length, tags, speaker, and translator comment — and
flags translations that are wrong *for that context*, even when they look fine in isolation.

The killer demo move: the tool infers context from the **String ID + metadata** when no comment
is given, and treats the comment as binding when it is. It also pulls the exact **style-guide
section** a string references (e.g. "See §6") and the matching **glossary** terms.

## Stack
- Streamlit (single-page UI, `streamlit run app.py`)
- OpenAI API for the LLM evaluation layer (model in `.env`)
- openpyxl / pandas for the XLSX I/O

## Input format (XLSX)
Columns (from `06_strings_to_translate.xlsx`):
`String ID · Source (EN) · Target (PL) · Speaker · Category · Comment · Max length · Tags`
Target columns are per-language. PL exists; DE will be added in a separate process.

## Pipeline (two layers)
1. **Deterministic checks** (no API key needed): max-length overflow, tag preservation
   (`[FR]`, `[RU]`, `[LAT]`, `[/FR]` …), placeholder preservation (`{placeholder}`, `{gender}`),
   empty-translation detection.
2. **LLM checks** (needs key): register/tone vs speaker+category, context appropriateness vs
   ID+comment (e.g. question form vs button label), terminology/glossary adherence, meaning fidelity.

Each issue has: severity (error / warning / suggestion), type, message, suggested fix.

## Conventions / decisions
- PL translations (incl. planted errors for demo) are authored by Gabriela.
- DE is out of scope for now — separate process later.
- Keep deterministic checks fast and offline so the app demos even without a key.
- Don't modify files in the parent loc kit; read them as context only.

## Reference assets (parent folder)
`01_style_guide.md`, `02_lore_bible.md`, `03_locations.md`, `04_characters.md`,
`05_glossary.csv`, `06_strings_to_translate.xlsx`

## DONE (Day 1, June 24 evening)
- **XLSX export** — replaced the CSV download. `build_xlsx_report()` in app.py. Columns map
  1:1 onto memoQ (`Status` = Rejected/Review/OK, `Comment` = note for the memoQ comment field).
  Rejected rows filled red, Review amber. **Demo = XLSX. memoQ round-trip = roadmap.**
- **Character bible** wired in — `load_character_bible` + `match_character` (by Speaker
  name-token overlap) in pipeline.py; new "Character descriptions (.md)" upload in the sidebar;
  the matched voice profile is injected into the LLM context for dialogue strings and shown in
  the "Context used" popover. This nails the challenge's "dialogue characters and their
  personality descriptions" definition of context.

### memoQ round-trip (roadmap / stretch only — NOT for the live demo)
The "real" flow a big LSP uses: push QA results back into memoQ as segments with status
**Rejected** and the AI note in the **memoQ comment**. Technical route without their server API:
read/write a bilingual **MQXLIFF** (or standard XLIFF 2.0), set segment status + comments,
reimport. Too many moving parts for 3 days — keep as a pitch slide, attempt only if the core is solid.

## Next ideas (post-MVP)
- Batch multiple strings per LLM call to cut cost.
- Lore-bible §III-style references (Roman numerals), not just style-guide §N.
- Local-model support (Ollama / LM Studio via OpenAI-compatible base_url) — added; expect
  weaker results than cloud models on the harder context/register checks.

## DONE (Day 1 evening, cont.) — paste field for character descriptions
Added an expandable "…or paste character descriptions" text area in the sidebar, as a
format-agnostic escape hatch (docx/PDF parsing is unreliable; pasting always works).
`parse_character_text()` in pipeline.py is tolerant of: `### Name` / `**Name**` headings,
`Name: desc`, `Name — desc`, and plain paragraphs starting with the name (one per line or
blank-line separated). Pasted entries are merged with any uploaded .md bible, then matched to
each Speaker the same way. Tested on 6 formats incl. a monster list. Matching logic is
format-independent; only the segmentation differs by source.

## DONE (Day 1 late) — flexible input + column mapping
The strings file no longer needs our exact headers. `load_strings` accepts .xlsx/.csv/.tsv
and picks the 'Strings' sheet OR the first sheet (no hardcoded sheet name). `auto_map()`
detects roles from arbitrary headers: ID synonyms (key/id/identifier…), source (source/en…),
and translation columns by language code/name via `LANG_NAMES` (en, ger→DE, ru, es, it, fr,
zh, ko, ja, pt-br, pl, …). A "🔧 Column mapping" panel (expanded when auto-detect is
incomplete) lets the user override every role + pick context columns (Speaker/Category/
Comment/Max length/Tags). Tested on a real-world header row
`key, en, ger, timeSensitiveScene, includeInSample, ru, es, it, fr, zh, ko, ja, pt-br, pl`
— all 10 languages detected, flags left unmapped, our original 8-column format still works.

## DONE — entity matching by source text (not just Speaker)
Character/entity profiles now also attach when the name appears in the SOURCE string, not
only when it's the Speaker. `match_entities()` in pipeline.py scans the source for any pasted/
bible name; matches are injected into the LLM prompt under "Named entities mentioned… respect
these facts (incl. grammatical gender)" and shown in the "Context used" popover. Added a system-
prompt rule to flag gender-agreement errors (e.g. a male entity translated with feminine forms).
Motivation: descriptive (non-dialogue) segments like "Wisdom / Gender: Male" — no Speaker, so the
old Speaker-only match never fired. Note: catching subtle PL gender agreement still depends on
model strength; llama3.1-8B may miss it — verify with gpt-4o / qwen2.5.

## Plan for tomorrow (Day 2) — explicit language selection before analysis
Goal: let the user pick which detected languages to analyze BEFORE running, to save time + tokens.
Note: a building block already exists — the "Translation columns to check" multiselect inside the
"🔧 Column mapping" panel already restricts which target columns run. The refinement:
- Surface it as a clear, prominent "Languages to analyze" control (friendly labels via lang_label:
  DE / RU / PL, not raw column names like ger/ru/pl), ideally outside/above the mapping expander.
- Default to all detected; allow quick select-all / clear-all.
- Show a live estimate of the workload before Run: rows × selected languages = N LLM calls
  (and a rough token/cost hint) so the user sees the saving.
- Persist the choice across reruns (session_state).

## DONE (Day 2) — rebrand + language selector + token counter + theme
- **Renamed to "Context Minder"** (page title, header). Translite triangle logo recreated as
  assets/logo.png (brand #fe8331) and shown in the header + as the page icon. NOTE: the original
  upload didn't reach disk as a file, so logo.png is a faithful PIL recreation — drop the exact
  PNG into mind-the-context/assets/logo.png to swap it.
- **.streamlit/config.toml** sets theme primaryColor #fe8331 (orange Run button + accents),
  light bg with a warm secondary (#fff4ec).
- **Languages to analyze** selector (the Day-2 plan): prominent multiselect with friendly labels
  (lang_label: DE/RU/PL…), default all, shows live workload estimate (rows × languages = segments
  / LLM calls). Run uses analyze_cols; restricting languages cuts tokens. Distinct from the
  mapping multiselect (which defines *which columns are translations*).
- **Token counter**: pipeline `_chat`/`llm_checks`/`analyze_row` now return prompt/completion
  token usage per row; app aggregates and shows "Tokens sent / received / LLM calls" metrics after
  the run. Local models report 0 if the server omits usage. Tested with a mock client (1800/240/6).

## DONE — .docx style guide support + generic paste examples
- Style guide uploader now accepts **.docx** (industry-standard format) alongside .md/.txt.
  pipeline.py: `parse_style_guide_docx()` reads paragraphs via python-docx, starting a new
  section on heading-styled or short numbered paragraphs ("6.5 Tags"); `load_style_guide()`
  dispatches by extension. app.py uses the dispatcher. Added python-docx to requirements.
  Tested: docx of our style guide parses to the same 34 sections as the markdown; §-references
  still resolve. Sample at sample_data/style_guide_sample.docx.
- Generic-ified the "paste character descriptions" placeholder (Captain Vale / Mara / The
  Merchant) so the tool no longer looks built for this one project.

## DONE — st.secrets fallback + full README + rename + UI clarity
- Game renamed "Embers of November" → "Sparks of November" in all loc-kit text files
  (style guide, lore bible, locations, characters, glossary). xlsx 'Read me' A1 still pending
  (file was locked/open). Folder name unchanged (mount root).
- `st.secrets` fallback added (`_secret()`): key resolved from pasted field → .env → Streamlit
  Secrets. Deploy strategy: NO owner key (cost risk) — users paste their own; Secrets only if a
  future deployer wants server-side key.
- UI: description rendered larger (1.12rem); added "ℹ️ What gets checked — with vs without an LLM"
  expander; clearer OpenAI key help; explicit Local-mode disclaimer (won't work on hosted app).
- README rewritten as a full project doc: description, what-gets-checked, features, local
  clone/venv/install/run, usage, input format, models/keys, Streamlit deploy, layout, limitations.
- Remaining for submission (Gabriela): test dataset (tonight), Streamlit deploy (tonight),
  video (tomorrow), submission form. Optional: 2-min pitch, swap real logo PNG.
