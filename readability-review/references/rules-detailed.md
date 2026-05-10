# Detailed rule reference

Detail for the rules most often cited in reviews. Use this when you've identified that a rule applies and you're about to suggest a fix — the extra context here helps you explain *why* a fix matters and offer a faithful before/after, rather than inventing one from general plain-English knowledge.

For a rule not covered here, fall back to the one-line summary in `guidelines.md` and the principles you already have. Don't try to manufacture extra detail you can't ground in the source.

Source: https://readabilityguidelines.co.uk/ — fetched and condensed from the canonical wiki pages. Quoted examples are illustrative; cite the rule ID, not this file.

## Table of contents

- [G1 — Choose easy and short words, not formal long ones](#g1)
- [G2 — Avoid jargon and buzzwords](#g2)
- [G3 — Write conversationally, in first person, using the active voice](#g3)
- [G5 — Average sentence length around 15 words](#g5)
- [G6 — Avoid complex sentence structures](#g6)
- [G7 — Explain specialist terms](#g7)
- [G8 — Write so all users can understand, regardless of expertise](#g8)
- [G9 — Help users understand specialist terms](#g9)
- [G10 — Use plain English even for highly literate audiences](#g10)
- [G18 — Never use vague words and jargon](#g18)
- [G19 — Avoid metaphors](#g19)
- [G20 — Don't use Latin](#g20)

---

## G1 — Choose easy and short words, not formal long ones <a id="g1"></a>

**Why it matters.** The guidelines aim for the reading comprehension of a 9-year-old. This isn't dumbing down — higher-literacy readers also scan, and shorter words are easier to scan. WCAG 2.0 itself calls for "the clearest and simplest language appropriate." The UN recommends plain language for communications.

**What to flag.** Formal Latinate words where a short Anglo-Saxon equivalent exists.

**Examples from the source.**
- "buy" not "purchase"
- "help" not "assist"
- "about" not "approximately"

**Common additions worth flagging.** "use" not "utilise"; "start" not "commence"; "show" not "demonstrate"; "end" not "terminate"; "enough" not "sufficient"; "buy" not "procure".

**Caveat.** Domain-specific terms aren't always replaceable — "approximately" in a regulatory context might be precise terminology. Note the substitution as an option, not a defect, when the formal term carries a specific meaning.

---

## G2 — Avoid jargon and buzzwords <a id="g2"></a>

**Why it matters.** Jargon is often vague rather than precise — it can mean different things to different readers, leading to misinterpretation or empty text. The guidelines describe jargon as "unlikely to be clear language."

**What to flag.** Phrases that sound substantive but don't commit to a specific action or meaning.

**Example from the source.**
> "Let's touch base in 10 and do some blue sky thinking." — uses jargon
> "Let's meet in 10 minutes to think of some ideas." — same meaning, clear

**Approach to fixes.** Don't just substitute one buzzword for another. Ask what the writer actually means and describe that. Be open and specific.

---

## G3 — Write conversationally, in first person, using the active voice <a id="g3"></a>

**Why it matters.** Picture your audience and write as if you were talking to them, with the authority of someone who can help and inform. Conversational tone reduces cognitive load; active voice puts the actor before the action, which most readers parse faster.

**What to flag.**
- Passive voice where the actor is known and could lead the sentence ("the form must be submitted by applicants" → "applicants must submit the form").
- Third-person institutional voice where first or second person would be more direct ("the company will contact you" → "we'll contact you").
- Bureaucratic register ("in order to facilitate" → "to help").

**Caveat.** Passive voice is sometimes the right choice — when the actor is unknown, irrelevant, or deliberately de-emphasised ("the file was deleted"). Flag passive voice as something to consider, not always to fix.

---

## G5 — Average sentence length around 15 words <a id="g5"></a>

**Why it matters.** Oxford Guide to Plain English, GOV.UK, and linguists converge on this. The source gives three thresholds:

- **15 words** — more likely to be comprehensible
- **25 words** — good maximum limit; comprehension drops above this
- **40+ words** — hard to comprehend easily

**What to flag.** Compute averages and the longest sentences if code execution is available. A document where the average is well above 15, or which has multiple sentences over 25, has a real problem worth quantifying. One sentence at 28 words isn't necessarily an issue; a pattern is.

**Approach to fixes.** Split long sentences into 2 or 3, or use bullet points. The source notes that a mix of slightly shorter and slightly longer sentences makes reading more interesting — don't push everything to 15.

**Specific advice for the report.** When flagging, give the actual numbers (average, max, count over 25) and quote the longest 2–3 sentences with locations. "Average sentence length is 23 words; 11 sentences exceed 25 words" is far more actionable than "sentences are too long."

---

## G6 — Avoid complex sentence structures <a id="g6"></a>

**Why it matters.** Complexity isn't just length. The source identifies two factors:

- **Number of clauses** — more clauses, more complexity
- **Distribution of associated words** — how easily the brain can connect words that together convey meaning

A 20-word sentence with three nested subclauses can be harder than a 30-word sentence with a simple subject-verb-object spine.

**Example from the source.**
> "The red fox jumped over the gate." — easier
> "The fox, which was red, over the gate jumped." — harder

**What to flag.** Multiple subordinate clauses; parenthetical asides that derail the main thought; verb phrases pushed far from their subjects; nested conditionals ("if X, then unless Y, except when Z").

**Approach to fixes.** Find the spine of the sentence (subject-verb-object), make that the main clause, and either split off the rest into separate sentences or move it to a clearer position.

---

## G7 — Explain specialist terms <a id="g7"></a>

**Why it matters.** Two common misconceptions: assuming who your audience is, and assuming they'll understand the technical terms you use. Anyone can land on the content — including experts in adjacent fields who don't know your specific terminology.

**What to flag.** Specialist terms used without definition, especially in content that's likely to attract general readers via search.

---

## G8 — Write so all users can understand, regardless of expertise <a id="g8"></a>

**Why it matters.** When you present a concept, explain its parts and processes. If a technical term is unavoidable, explain it — and make sure the surrounding language is plain.

**Approach to fixes.** Don't just gloss the term in isolation; check that the sentence around it doesn't compound the difficulty. A defined jargon word inside a complex passive sentence is still hard to read.

---

## G9 — Help users understand specialist terms <a id="g9"></a>

**Three options from the source:**

1. Link to an existing definition (could be external).
2. Add an explanatory definition after using the term.
3. Use a plain alternative.

**Example from the source.**
> Original: "It is a Palladian style stone building, and contains a number of splendid paintings and much fine wood-carving."
> With link: "It is a stone building in the [Palladian style](...). It contains a number of splendid paintings..."
> With explanation: "It is a Palladian style stone building... Palladian style architecture features include columns, symmetry and decorative arches."

**What to flag.** Specialist terms used as if every reader knows them, with no link, gloss, or alternative.

---

## G10 — Use plain English even for highly literate audiences <a id="g10"></a>

**Why it matters.** Evidence shows experts also prefer plain English. Higher-literacy readers scan web pages too — and they tend to have more to read, less time to read it. Plain language saves expert readers time; it doesn't insult them.

**Source quote (paraphrased).** People with the highest literacy levels and greatest expertise tend to have to read the most. They don't have time for lengthy, complex content.

**What to flag.** "We can use jargon because our audience is technical" reasoning. The argument doesn't survive contact with usability evidence — Loranger (NN/g 2017), Schulman et al (2020), and others show experts comprehend faster and trust more when content is in plain English.

---

## G18 — Never use vague words and jargon <a id="g18"></a>

**Why it matters.** Vague words mean nothing — they waste time, irritate users, and can make readers trust the content less. The source is unusually emphatic here: "Vague words mean nothing."

**Specific words to flag (from the source).** This is the canonical list — cite directly when flagging.

| Word | When to flag | Suggested fix |
|---|---|---|
| agenda | unless it's a meeting agenda | be specific about the priorities |
| advancing | almost always | what specifically is being moved forward? |
| collaborate | almost always | "working with" |
| combating / countering / tackling | unless literal (sport, military) | what action is actually being taken? |
| commit / pledge | almost always | "we will X" or "we won't X" — be specific |
| deliver | unless literal (pizzas, post, services) | "improve", "reduce", "build" — what's the actual verb? |
| deploy | unless military or software | what's actually being put into use? |
| dialogue | almost always | "talk to", "speak to", "discuss" |
| disincentivise / incentivise | almost always | "discourage" / "encourage" |
| empower | almost always | what specifically enables the user to do? |
| facilitate | almost always | be specific about how you're helping |
| focusing | almost always | what's the action? |
| foster | unless about children | "encourage", "support", "build" |
| impact (verb) | almost always | "affect", "change", "influence" |
| initiate | almost always | "start", "begin" |
| key | unless it unlocks something | "important", "main", "central" |
| land (verb) | unless aircraft | what's being made to happen? |
| leverage | unless financial sense | "use" |
| liaise | almost always | "work with", "talk to" |
| overarching | almost always | usually the word adds nothing — cut it |
| progress (verb) | almost always | what's the action? |
| promote | unless ad/marketing campaign | what specifically is being supported? |
| robust | almost always | "strong", "reliable", "well-tested" |
| signposting | almost always | "instructions", "directions", "links" |
| slimming down / streamline | almost always | what specifically is being removed or simplified? |
| strengthening | unless literal (bridges) | "improving" — be specific |
| transforming | almost always | what's actually changing? |
| utilise | almost always | "use" |

**Approach to fixes.** Don't just substitute. Ask what the writer means and describe that.

---

## G19 — Avoid metaphors <a id="g19"></a>

**Why it matters.** Metaphors don't say what you actually mean. They translate poorly, slow comprehension, and confuse non-native speakers. They also fail when read literally by screen readers or translation tools.

**Specific phrases to flag (from the source).**

- "drive" — only literal vehicles, not schemes or people
- "drive out" — unless it's cattle
- "going forward" — it's unlikely you're giving travel directions
- "in order to" — superfluous; use "to"
- "ring fencing" — unless you're putting up a fence in a circle

**Common additions.** "moving the needle", "low-hanging fruit", "boil the ocean", "circle back", "level up", "double down", "in the weeds".

---

## G20 — Don't use Latin <a id="g20"></a>

**Why it matters.** Latin abbreviations and phrases are read inconsistently by screen readers and unfamiliar to many readers. The source treats this as an absolute: "Do not use Latin."

**Specific replacements (from the source).**

- "per annum" → "each year"
- "eg" / "e.g." → "for example"
- "ie" / "i.e." → "that is"
- "pro bono" → "for free"

**Common additions.** "etc." → "and so on" (or rewrite); "vs." → "versus" or "compared with"; "via" → "through" or "using"; "ad hoc" → "as needed" or "one-off"; "de facto" → "in practice".

**Caveat.** Some Latin terms are now genuinely English ("via" is borderline; "etc." is widely understood). Apply judgment — if a plainer alternative is available, use it.
