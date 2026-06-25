# 🎯 Context Minder

**Context-aware localization QA.** Most QA tools check a translation in isolation. Context Minder
reads the **context** around each string — the string ID, category, max length, tags, speaker and
translator comment — together with your **style guide**, **glossary** and **character descriptions**,
and flags translations that are wrong *for their context*, even when they look fine on their own.

Built for the GenAI in Localization Hackathon (MAD 3, Solo Builder track) — challenge #1,
*"Mind the Context" (Quality Pipeline)*.

---

## Why it's different

- **Infers context from the String ID + metadata** when no comment is given
  (`ui_combat_attack`, max 14 → a button: short, imperative), and treats the translator
  **comment as binding** when it is given.
- **Pulls the exact style-guide section** a string references (a comment saying "See §6"
  injects only §6 into the check).
- **Matches glossary terms** that appear in the source and checks the prescribed target form.
- **Matches character / entity profiles** — by the `Speaker` column *and* by names appearing in
  the source text — so it can catch e.g. a male entity rendered with feminine forms in descriptive
  (non-dialogue) segments.

## What gets checked

**Always — no API key needed (fast, deterministic rules):**

- Max-length / UI overflow
- Tag preservation — `[FR]…[/FR]`, `[u]`, `[one]/[few]/[many]/[other]`, `[ms]`/`[fs]`, …
- Placeholder preservation — `{QUANTITY}`, `{gender}`, `{character.firstName}`, …
- Mob gender-variant pair — both `[ms]` and `[fs]` present
- Empty / untranslated segments

**With an LLM — needs an API key or a local model:**

- Register & tone vs the speaker and category
- Context fit vs the string ID + translator comment (e.g. question form vs button label)
- Terminology / glossary adherence
- Meaning fidelity & grammatical gender, using matched character / named-entity facts

Each issue carries a severity (🔴 error / 🟠 warning / 🟡 suggestion), a type, a message and a
suggested fix, tagged ⚙️ rule or 🧠 llm.

## Key features

- **Flexible input** — `.xlsx` / `.csv` / `.tsv`; no fixed sheet name or column names.
  Auto-detects ID, source and translation columns (by language code/name), with a
  **🔧 Column mapping** panel to override anything and pick context columns.
- **Languages to analyze** — pick a subset of detected languages before running, with a live
  workload estimate, to save time and tokens.
- **Token counter** — reports tokens sent / received and LLM calls after each run (cost visibility).
- **Style guide in `.docx` or `.md`**, glossary `.csv`, character descriptions by **file upload or
  paste** (paste accepts headings, `Name: desc`, `Name — desc`, or plain paragraphs).
- **XLSX report** whose columns map 1:1 onto the **memoQ** feedback pattern
  (`Status` = segment status, `Comment` = the memoQ comment-field note; Rejected rows highlighted).
- **Cloud or local models** — OpenAI, or any OpenAI-compatible local server (Ollama / LM Studio).
- Deterministic checks always run, so the tool is useful even with **no API key at all**.

---

## Run it locally

Requires Python 3.10+.

```bash
# 1. Get the code
git clone <your-repo-url>
cd context-minder            # or: cd mind-the-context

# 2. Create and activate a virtual environment
python -m venv .venv
source .venv/bin/activate     # Windows: .venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. (Optional) add an API key for the LLM checks
cp .env.example .env          # then paste your OPENAI_API_KEY into .env

# 5. Run
streamlit run app.py
```

The app opens at `http://localhost:8501`.

> If PowerShell blocks the venv activation, run once:
> `Set-ExecutionPolicy -Scope CurrentUser RemoteSigned`

## Using it

1. **Sidebar → Strings:** upload your strings file. Try `sample_data/demo_strings_PL_with_errors.xlsx`
   for an instant demo.
2. **Context assets (optional but recommended):** glossary `.csv`, style guide `.docx`/`.md`, and
   character descriptions (upload `.md` or paste fragments).
3. **Engine:** choose **OpenAI (cloud)** and paste a key, **Local (Ollama / LM Studio)**, or leave
   it off to run deterministic-only.
4. **Column mapping:** review the auto-detected mapping; fix anything that's off.
5. **Languages to analyze:** trim to the languages you want this run.
6. **▶ Run QA.** Review the table, expand any row for details and the exact **Context used**, see the
   **token counter**, and download the **XLSX report**.

## Input format

A sheet of strings with, at minimum, an **ID** column, a **source** column, and one or more
**translation** columns. Column names are flexible — translation columns are detected by language
code/name (`en`, `ger`→DE, `pl`, `ru`, `es`, `fr`, `zh`, `ja`, `pt-br`, …) or `Target (XX)`, and you
can remap everything in the **Column mapping** panel. Optional context columns: `Speaker`,
`Category`, `Comment`, `Max length`, `Tags`. Every selected translation column is checked as a
separate target language in one pass.

## Models & API keys

- **OpenAI (cloud):** paste your own key in the sidebar (used only for that session, never stored),
  or keep it in a local `.env` (`OPENAI_API_KEY=…`), or — when deployed — in Streamlit **Secrets**.
- **Local (Ollama / LM Studio):** no key, nothing leaves your machine. Expect weaker results than a
  strong cloud model on the subtler register/gender checks. **Local mode only works when you run the
  app on your own machine** — it can't reach `localhost` from a hosted deployment.
- **No engine:** the deterministic checks still run.

## Deploy (Streamlit Community Cloud)

Push the repo to GitHub, then on [share.streamlit.io](https://share.streamlit.io) connect the repo
and point it at `app.py`. The public app URL is what you share. The app runs **without an owner key**
by default (deterministic checks + "paste your own key" for LLM checks), so hosting costs you nothing.
If you ever want server-side LLM checks, add `OPENAI_API_KEY` in the app's **Secrets** (and set a
spending limit on the key).

## Project layout

```
app.py                  Streamlit UI
pipeline.py             QA engine (context building + checks), reusable without the UI
requirements.txt
.env.example            copy to .env for a local key
.streamlit/config.toml  theme (brand colour)
assets/logo.png         header logo
sample_data/            demo strings + a sample .docx style guide
CLAUDE.md               project memory / notes
```

## Notes & limitations

- Catching subtle grammatical-gender or register errors depends on model strength; a small local
  model (e.g. llama3.1-8B) may miss them — verify with a stronger model.
- The memoQ round-trip (writing segment status + comments back via MQXLIFF) is a roadmap item; the
  current deliverable is the XLSX report whose schema maps onto it.
