# GenAI in Localization Hackathon — Tasks & Rules

> Source: https://custom.mt/wp-content/uploads/2026/06/Hackathon-Tasks.pdf
> Saved 2026-06-24. Faithful transcription of the official tasks PDF.

## Instructions for the participants

GenAI in Localization Hackathon is a great way to showcase your builder skills and bring forth
creativity for the next chapter in the industry beyond text translation and LLM orchestration. To
participate in the hackathon, you will need a model-assisted development tool, such as ChatGPT,
Codex, Cursor, GitHub Copilot, Claude Code, Loveable, Base44, Replit, Bolt, Google AI Studio,
OpenClaw, or any other that you find convenient.

1. Hackathon challenges will be announced at **15:30 Paris time, June 24** on the GenAI in
   Localization conference broadcast. There are **4 vetted [build an app] challenges** based on
   real business needs designed by experienced localization directors.
2. You will have **48 hours** to complete the challenge and build the corresponding app of your
   choice. **Deliver the app before 16:00 Paris time, Jun 26, 2026** by completing the form.
   They recommend adding a link to a **short video** of your app, especially for tools with a
   minimalist frontend. You can also add **test datasets** so visitors can see your tool in action.
3. Completed apps will be displayed on https://custom.mt/genai-in-localization-2026/ and voted on
   by the participants and the judges, with your name and optional team logo.

### Comparison / judging criteria
   a. **Ability to complete the challenge**
   b. **User experience**
   c. **Presentation**

### Prize pool: **$1,000**

---

## Challenges

### 1. "Mind the Context" (Quality Pipeline) — *our pick*
Context-aware translation remains a largely unsolved problem in our industry, and one that becomes
increasingly important as more content is translated with AI. In this challenge, build an app that
**validates the translation in-context, on top of it being linguistically accurate**. Pick your
definition of context: developer notes, UI screenshots and HTML, **dialogue characters and their
personality descriptions**, a video with frames taken every 2 seconds, images of products in an
e-commerce catalog, PDF blueprints with formulas, or even an audio stream.

You can think of the quality pipeline as a **quick and low-latency step that happens before
translations go live**, or as a **post-publishing corrective process**.

*By Melanie Heighway*

### 2. "Find the Right Model" (Evaluation tool)
In a world where new models become available every two weeks, some companies use all of them.
Different languages, tasks and content types require optimal models for cost, latency, expected
quality. Build a **"Translation provider selection engine"** that helps select the best MT provider.
Requirements:
- **Flexible**: various business rules can be applied for decision-making
- **Automated**: humans should only be involved when required
- **Explainable**: decisions are motivated

*Suggested by Nicolas Jadot, Trendyol*

### 3. "Are We Fit for This Market" (Website reviewer)
Build an app that reviews and scores multilingual websites for linguistic quality, terminology
consistency, cultural adaptation and other criteria. It ingests HTML web pages, looks at them
holistically and generates a report/dashboard that helps content groups determine what to improve.
Advanced:
- Sync strings parsed from the website with strings in the translation memory, so the app finds the
  exact position of the text within the TMX and fixes it.
- Allow human review for proposed changes and an approval process.

*Suggested by Hyunjoo Han, Autodesk*

### 4. "Localization Manager's Dream" (Capacity planner)
A localization team supports multiple requests from various teams — classic file translation, plus
complex engineering jobs with checks across tools, team alignment, or new workflows. Build a
**planner/ticketing system tailored for localization, operating via a Slack bot** that supports both
the loc team and stakeholders (requesters and management).
Requirements:
- **Flexible**: supports an increasing number of use cases / request types automatically
- **Human in the loop**: knows when to loop in a team member
- **Ease of use**: stakeholders can interact with it directly and get useful answers

*Suggested by Giulia Tarditi, Revolut*

---

## How our build maps to Challenge 1 (notes)
- **"Validates in-context AND linguistically accurate"** → two layers: deterministic checks
  (length/tags/placeholders) + LLM checks (register, context-fit, terminology, meaning). ✓
- **"Pick your definition of context"** → our definition: **developer notes (Comment column)**
  + **dialogue characters and their personality descriptions (Speaker + character bible)**.
  Deliberately text-metadata, not screenshots/video/PDF — the right scope for solo / 3 days.
- **"Low-latency pre-check vs post-publishing corrective"** → deterministic = fast pre-check;
  LLM = deeper corrective pass. Good framing for the pitch.
- **TODO that closes the match**: wire in `../04_characters.md` (character bible) so dialogue
  strings get personality context by Speaker.

## Judging criteria → what to optimize
- **Ability to complete the challenge** → make the core pipeline visibly work on real data.
- **User experience** → clean Streamlit UI, instant demo dataset, clear flagged report.
- **Presentation** → the optional 2-min pitch + short video walkthrough. Lead with the
  context-from-ID/metadata differentiator and the memoQ-mapped export story.
