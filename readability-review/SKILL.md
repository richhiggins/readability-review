---
name: readability-review
description: Review a document against the Readability Guidelines (readabilityguidelines.co.uk) and produce a structured report with a prioritised checklist of fixes. Use this skill whenever the user asks for a "readability report", "readability review", "readability check", or asks to evaluate content against the Readability Guidelines, Content Design London guidelines, or plain-English/clear-language standards. Also trigger when the user pastes copy or shares a document and asks whether it's readable, accessible, plain English, or follows good content design — even if they don't say "Readability Guidelines" by name. Handles plain text, uploaded files (.docx, .pdf, .txt, .md, .html), and URLs.
---

# Readability review

Reviews a document against the 83 evidence-based rules in the Readability Guidelines and returns a structured report plus a prioritised action checklist.

## What this skill is for

The Readability Guidelines (readabilityguidelines.co.uk) are an evidence-based content style wiki maintained by Content Design London. They cover plain English, grammar, audience considerations, and content design — not generic "readability scores" like Flesch–Kincaid. The point of this skill is to apply *those specific rules* with citations, not to produce a vague "this could be clearer" critique.

The full rule set lives in `references/guidelines.md`. Read that file at the start of any review — it contains the 83 numbered guidelines (G1–G83) you'll cite from.

## Workflow

### 1. Get the document

The user may provide content in several ways:

- **Pasted text** in the conversation — work with it directly.
- **An uploaded file** in `/mnt/user-data/uploads/` — read it. For `.docx` and `.pdf`, use the appropriate skill (docx skill, pdf-reading skill) to extract text. For `.txt`, `.md`, `.html`, read directly.
- **A URL** — fetch it with `web_fetch`.
- **No document yet** — ask the user to share one. Don't generate a generic explainer about the guidelines unless they ask for that.

### 2. Read the guidelines reference

Open `references/guidelines.md` before analysing anything. The skill is only useful if the report cites specific rules (G1, G18, G53, etc.) — guessing at rule IDs from memory will produce broken citations.

For the most-cited rules (G1–G3, G5–G10, G18–G20), `references/rules-detailed.md` has fuller source-grounded detail: the rationale, specific words/phrases to flag, and faithful before/after examples. Read it when you're about to suggest a fix for any of those rules — it's the difference between citing the rule and explaining *why* the fix matters. For other rules, work from `guidelines.md` and general principles.

### 3. Analyse the document

Work through the rules section by section (Clear Language → Grammar → Audiences → Content Design). For each rule:

- Decide if it applies to this document. Skip rules about social media if it's a report; skip link rules if there are no links.
- Look for concrete violations with evidence — quote the offending phrase or describe the location.
- Don't list rules the document follows. The default report is a list of *issues found*, not a full audit. (If the user explicitly asks for full coverage, switch modes.)

For sentence-length and complexity checks (G5, G6), compute rather than guess if you have code execution available — a quick Python pass over the text gives accurate average and max sentence lengths. Otherwise, eyeball the longest sentences.

### 4. Produce the report

The report has three parts. Keep it tight — the goal is something the user can act on, not an essay.

**Summary** — 2–4 sentences. What's the document about, who's it for (if inferable), and what's the headline verdict? "This is mostly clear, but four issues recur throughout" is more useful than "Some aspects of the writing could be improved."

**Findings** — grouped by section (A/B/C/D), with each finding showing:
- The guideline ID and short name (e.g. `G18 — Vague words and jargon`)
- A specific example from the document, quoted or located
- A concrete suggested fix where possible

**Action checklist** — a prioritised list of fixes. Order by impact (issues that recur throughout > one-off issues > stylistic preferences). Each item should be specific enough to do without having to re-read the report — "Replace 9 instances of 'leverage' with 'use'" beats "Address jargon."

### 5. Match the user's requested format

The user might ask for the report inline, as a markdown file, as a Word doc, or as a PDF. Default to inline markdown. If they ask for a file, use the relevant skill (docx, pdf) and follow normal file-handling rules — write to `/mnt/user-data/outputs/` and present with `present_files`.

## Report structure

Use this template. Adapt the headings to the user's chosen format (e.g. proper Heading styles in a `.docx`).

```markdown
# Readability review: [document title or first few words]

## Summary
[2–4 sentences: what the document is, who it's for if inferable, top-level verdict.]

## Findings

### A. Clear language
- **G[X] — [rule short name]**
  - Issue: [quote or location]
  - Suggested fix: [concrete rewrite or direction]

### B. Grammar points
[same structure]

### C. Audiences, devices, channels
[same structure — often empty for non-public-facing docs]

### D. Content design specifics
[same structure — often empty for plain-text docs]

## Action checklist
1. [Highest-impact fix — e.g. "Shorten the 8 sentences over 30 words listed above (G5)."]
2. [Next fix]
3. [...]

---
*Reviewed against the Readability Guidelines (readabilityguidelines.co.uk).*
```

## Tone of the review

The review should sound like a thoughtful editor, not a linter. The guidelines are evidence-based but not absolute — context matters. A medical leaflet for clinicians can use more specialist terms than one for patients; a marketing landing page lives by different conventions than a government form. Note when a "violation" is defensible in context rather than mechanically flagging it.

Be direct about issues but not preachy. The user wants to fix things, not be lectured about plain English.

## Edge cases

- **Very short documents (<100 words)**: a full report is overkill. Give a short bulleted assessment with rule IDs and skip the multi-section structure.
- **Very long documents (>5,000 words)**: don't try to flag every instance. Identify the top 5–8 recurring issues with 2–3 examples each, then note in the action checklist that those patterns appear throughout.
- **Documents that aren't really prose** (tables, code, forms): apply only the rules that fit and say so explicitly.
- **Non-English documents**: the guidelines are UK-English-specific. Note this and offer to assess what does transfer (sentence length, structure, jargon principles) versus what doesn't (specific UK conventions like dates).
- **The user wants full coverage, not just issues**: switch to a mode where you confirm rules followed correctly as well as ones violated. This is more work and produces a longer report — only do it on request.

## What this skill does not do

- It doesn't compute Flesch–Kincaid or other reading-grade scores. Those aren't part of the guidelines. If the user asks, mention them as a supplementary tool, but the report stays grounded in G1–G83.
- It doesn't rewrite the whole document. The output is a review with a checklist; if the user wants a full rewrite, that's a separate request and you should confirm before doing it.
- It doesn't enforce a different style guide (AP, Chicago, GOV.UK style guide, company style). Some guidelines conflict with those — for example, G46 says use numerals for all numbers, which contradicts AP. Note conflicts where they're likely to matter, and let the user decide which guide wins.
