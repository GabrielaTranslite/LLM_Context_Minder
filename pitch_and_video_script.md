# Context Minder — 2-minute pitch & video script

For: GenAI in Localization Hackathon (MAD 3) · Challenge #1 "Mind the Context"
Judging criteria: (1) ability to complete the challenge, (2) user experience, (3) presentation.

---

## Part 1 — The 2-minute pitch (spoken)

Target ~2:00 at a calm pace (~270 words). Speaker notes in *(italics)*. If you run long,
cut the paragraph marked **[CUT IF NEEDED]**.

> **The problem.** *(open with the pain — judges are localization people, they've lived this)*
> Every localization team knows the worst kind of bug: a translation that is perfectly correct —
> and completely wrong. "Save" translated as a noun when it's a button. A male creature described
> with feminine endings. A formal line where the character is being vulgar. Each one passes
> spell-check and a glossary check, and fails the player. As we translate more with AI, there's
> simply more of this — and it's exactly the part current QA tools don't catch.
>
> **What it is.** *(say the name clearly, slow down)*
> Context Minder is a quality pipeline that reads the **context** around every string — not just
> the words.
>
> **Why it's different.** *(this is the heart — land it)*
> It infers context from the string ID and metadata: `ui_combat_attack` with a 14-character limit
> is a button, so it must be short and imperative. It treats the translator's comment as binding.
> It pulls the exact style-guide section a string points to, matches your glossary, and — the part
> I'm proudest of — it attaches the right **character or entity profile**: by who's speaking, and by
> names appearing in the source. That's how it catches a gender or register error a generic checker
> never could.
>
> **[CUT IF NEEDED] How it runs.** Two layers: fast deterministic checks — length, tags,
> placeholders, plural and gender tags — with zero API cost, and an LLM layer for register,
> terminology and meaning. It takes any spreadsheet: it auto-detects your columns and languages,
> you pick which languages to run to control spend, and it reports exactly how many tokens you used —
> because cost matters now.
>
> **The close.** *(slow, confident)*
> The output is an Excel report whose columns map one-to-one onto memoQ — segment status and
> comment — ready to push back into your workflow. Context Minder doesn't just tell you a
> translation is wrong. It tells you it's wrong **for its context**, and why. Thank you.

**Delivery checklist**
- Practice once with a timer; the **[CUT]** paragraph is your buffer.
- Have the live app open on the demo string before you start, so you can gesture to it.
- One sentence per idea. Pause after "wrong for its context, and why."

---

## Part 2 — Video walkthrough script (~2–3 min)

Record at 1280×720+ with the browser zoom so text is readable. Use a real example (the demo
dataset or your test set). Narration in quotes; on-screen action in *(italics)*.

**0:00 — Title (5s)**
*(app open, logo + "Context Minder" visible)*
"This is Context Minder — context-aware localization QA. Let me show you what that means."

**0:05 — The problem in one line (10s)**
*(hover the "ℹ️ What gets checked" expander, open it briefly)*
"Most QA checks a translation in isolation. This one reads the context around each string — and
checks two ways: deterministic rules with no API cost, and an LLM layer for the subtle calls."

**0:20 — Load + auto-mapping (25s)**
*(drag the strings file into the sidebar uploader)*
"I drop in a strings file — any spreadsheet. It auto-detects the columns…"
*(open the 🔧 Column mapping panel)*
"…the ID, the source, and each language by its code. I can remap anything, and point it at the
context columns — speaker, comment, max length, tags."

**0:45 — Languages + context assets (20s)**
*(show the Languages to analyze selector; deselect one language)*
"I pick which languages to run — fewer means fewer tokens, and it shows the workload up front."
*(upload glossary + style guide .docx; paste a character description)*
"Then I add context: glossary, the style guide as a Word doc, and character descriptions — uploaded
or just pasted."

**1:05 — Run (10s)**
*(paste API key or note deterministic mode; click ▶ Run QA)*
"Run."

**1:15 — Results: the payoff (45s)**
*(point to the metrics row)*
"Here are the flags by severity."
*(expand one flagged row — ideally a context/gender catch)*
"This one looks fine in isolation, but…"
*(open the "Context used" popover)*
"…look here — it pulled the style-guide section, matched the glossary term, and attached the
character profile. That's *why* it's flagged. A generic checker would have passed it."

**2:00 — Tokens + export (20s)**
*(point to the token counter)*
"It reports exactly the tokens sent and received — cost is visible."
*(click Download QA report, open the XLSX)*
"And the report maps straight onto memoQ: segment status and the comment, ready to reimport."

**2:20 — Close (10s)**
"Context Minder — it doesn't just say a translation is wrong. It says it's wrong for its context,
and why."

**Recording tips**
- Do a dry run first; pre-load the file so there's no waiting on screen.
- If using the LLM layer live, pick a fast model (gpt-4o) and just 1–2 languages so it's quick.
- Keep it under 3 minutes; the single most important beat is the **"Context used"** popover —
  linger there.
