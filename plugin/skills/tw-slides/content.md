# TW Slides — Content Patterns

Content patterns for the **AI Survey** pitch deck. This is the generic, product-level template. When building a deck for a specific client, source the facts from that client's folder in the `client-wiki` repo (`clients/{name}/`) and fill them into the patterns below.

For every slide: follow the pattern, render on the named slide type (see `slide-types/`), and apply `writing-rules.md` to every line.

---

## Deck spine

| # | Slide | Slide type | Variant |
|---|-------|------------|---------|
| 1 | Situation | `left-third-title` | `columns` (default) or `bullets` |
| 2 | Objectives | `left-third-title` | `bullets` (numbered) |
| 3 | Turing Works approach: Survey → Assembly | `left-third-title` | `bullets` (not numbered) |
| 4 | Opportunities already identified | `card-list` | — |
| 5 | How the Survey validates and finds more | `process-stages` | — |
| 6 | Risk reversal | `left-third-title` | `bullets` (not numbered) |
| 7 | What you get: deliverables package | `card-list` | — |
| 8 | Next steps | `left-third-title` | `bullets` (numbered) |

---

## Slide 1 — Situation

### Slide type
`left-third-title`

### Variant
`columns` with 3 cards (default) — when the situation splits into parallel themes or teams. `bullets` — when the situation is one topic with nested sub-issues. Column count can flex to 2 or 4 if the content demands it.

### Purpose
Show the client we understand their world. Lead with their problem, not our method.

### Action title pattern
Name the scaling pressure they're under in one conclusion. Example shape: *"{{Client}} is scaling {{growth metric}} but {{constraint}} is multiplying admin load"*.

### Body content
2–3 sentences describing the current state. Include:
- Size / scale of the operation (specific numbers)
- Growth rate or trajectory
- The manual work that compounds as they scale — the specific systems, reports, or processes causing drag

### Section subtitle (left panel)
"Understanding the client's\ncurrent state and growth pressures"

### Source
"Source: Discovery calls with {{stakeholder name(s)}}, {{date}}"

### Source material in `client-wiki`
- `clients/{name}/{name}.md` — hub page, especially the Current State section
- `clients/{name}/wiki/meetings/` — discovery call notes
- `clients/{name}/wiki/research/` — company profile, scale indicators

### Writing rules reminders
- Use the client's own language for their pain points — lift phrases from transcripts
- Quantify everything you can (headcount, units, growth rate, hours)
- No solution language on this slide — that comes in slide 3

---

## Slide 2 — Objectives

### Slide type
`left-third-title`

### Variant
`bullets` with `numbered: true` — numbered teal circles, each with a bold title and a continuation sentence. Numbered (not dotted) because objectives are a discrete, finite set the sponsor can count off.

### Purpose
Frame the engagement around outcomes the client cares about, not solutions we sell. Must reflect what was agreed on the conceptual agreement call.

### Action title pattern
One conclusion naming the outcome the engagement is built around. Example shape: *"{{Client}} wants to {{primary outcome}} without {{primary constraint}}"* — e.g. *"Ballpoint wants to double client load without doubling the team"*.

### Body content
1–4 numbered objectives (3 is the typical sweet spot). Each = **bold title (3–8 words)** + continuation sentence (15–30 words). Outcome language only — name the *result*, not the *mechanism*.

Source the objectives from what the sponsor said on the conceptual agreement call. If they named more than 4, pick the ones with the clearest signal of success and fold the rest into continuation text.

Common shapes for ops-heavy DTC / services businesses:
- **Scale without scaling headcount** — handle {{growth metric}} of additional volume on the current team
- **Replace manual reporting** — leadership sees {{metric}} without {{report owner}} stitching it together each week
- **Take pressure off {{specific function}}** — reduce the {{recurring task}} load on {{team}} so they can focus on {{higher-value work}}
- **Build {{capability}}** — for capability or maturity goals where success is qualitative (e.g. "be able to spin up a new market without a new ops hire")

### Section subtitle (left panel)
"What {{client}} wants to achieve\nover the next {{horizon}}"

### Source
"Source: Conceptual agreement call with {{sponsor}}, {{date}}"

### Source material in `client-wiki`
- `clients/{name}/wiki/meetings/` — especially the conceptual agreement / discovery call
- `clients/{name}/{name}.md` — Objectives, Measures of Success, and Value sections on the hub

### Writing rules reminders
- Outcomes, not solutions. "Reduce manual ops burden" — not "implement automation platform".
- Bold the verb in each objective so the outcome scans fast
- Tense: future-looking ("wants to…", "will…")
- Prefer measurable objectives, but capability or maturity goals can be subjective if that's what the sponsor said — lift their framing rather than forcing a metric onto it
- Use the sponsor's own phrasing from the call transcript wherever possible

---

## Slide 3 — Turing Works approach: Survey → Assembly

### Slide type
`left-third-title` (section label "Approach" or "Turing Works")

### Variant
`bullets` with `numbered: false` — three teal-dot top-level items, one per paragraph, each with a bold lead-in phrase.

### Purpose
Explain the two-part offering at a high level. Anchor the deck in the Survey (what this engagement is) while signalling that Assembly exists if they want us to implement.

### Action title pattern
*"Turing Works finds and validates AI opportunities (Survey), then implements them (Assembly) — this engagement covers the Survey"*.

### Body content
Three bullets:
1. **Frame the problem space** — COOs and ops leaders understand the goal but can't pinpoint which workflows need work. Generic AI consultancies produce slide decks; few translate into live automation.
2. **The Survey does the diagnosis** — a prioritised roadmap of use cases worth at least 1 FTE in implementable value, with effort and ROI estimates per opportunity.
3. **Assembly is optional** — if the client wants us to implement what the Survey finds, we do; Survey work is discounted against Assembly scope.

### Section subtitle (left panel)
"How Turing Works turns\nAI ambition into live automation"

### Source
Omit (this is our offering, not a claim about client data).

### Source material in `client-wiki`
None — this slide is product-level, identical across clients.

### Writing rules reminders
- Do not inflate the offering with modifiers ("world-class", "game-changing") — confident, not salesy
- The discount on Assembly is a real commercial term, not a throwaway — phrase it clearly

---

## Slide 4 — Opportunities already identified

### Slide type
`card-list`

### Purpose
Prove the opportunities are real by naming 3–5 concrete ones surfaced from pre-work alone. This is the credibility slide — tangible value before the Survey even starts.

### Action title pattern
*"Pre-work has already surfaced {{$X}} in potential annual savings across {{N}} opportunities"*.

### Lead subtitle (teal, optional)
*"Desk research from one discovery call, before any interviews or workshops"*.

### Card pattern (3–5 cards)
Each card has:
- **Title:** the opportunity name (e.g. "Toll reconciliation automation")
- **Metric:** estimated annual value or time saved (e.g. "~$18k/yr" or "~400 hrs/yr")
- **Description:** 1–2 sentences — what the manual work is today, what the automation would replace
- **Category:** the function or system it touches (e.g. "Finance", "Ops", "Data")

### Source
"Source: {{source of savings estimate — benchmark, client data, analyst estimate}}"

### Optional footer
Link to an interactive opportunity map for the client (if built). E.g. *"See live map: {{url}}"* — this becomes a living artefact referenced again in slide 7.

### Source material in `client-wiki`
- `clients/{name}/wiki/use_cases/` — each `YYYY-MM-DD_hN-*.md` file is a candidate opportunity; frontmatter has `pain_point_summary`, `kpi`, `fte_value`, `priority`, `confidence`
- `clients/{name}/wiki/use_cases/_hypotheses.base` — priority-ordered view; pick the top 3–5
- `clients/{name}/wiki/use_cases/_assessment-approach.md` — the narrative framing for the assessment

### Writing rules reminders
- Title + metric separated by whitespace, not em dash or pipe
- Metrics must be numeric and sourced — no "significant" or "substantial"
- Keep descriptions concrete: name the tool, the team, or the report being replaced

---

## Slide 5 — How the Survey validates them and finds more

### Slide type
`process-stages`

### Purpose
Show the Survey method is rigorous without being heavy. Three stages, each short, each producing an output.

### Action title pattern
*"AI-powered research, {{N}} interviews, and a prioritisation workshop turn hypotheses into a scored roadmap"*.

### Subtitle (teal, below title)
*"Every opportunity scored against {{client}}'s priorities, with effort and ROI estimates leadership can decide on"*.

### Stage 1 — Research
- Week label: "Pre-engagement"
- Activity title: "AI-powered research"
- Bullets:
  - Industry, tech stack, and competitor AI adoption analysis
  - Job postings mined for pain and growth signals
  - Pattern library of AI use cases by industry, department, and tech stack applied to {{client}}'s shape
- Output: "Draft hypothesis list with effort and ROI estimates"

### Stage 2 — Interviews
- Week label: "Week 1"
- Activity title: "3× AI-powered interviews (30 min each)"
- Bullets:
  - Sponsor — strategy and success criteria
  - Ops lead — workflows and pain points
  - Key operator — day-to-day detail on the highest-friction processes
- Output: "Validated and expanded opportunity list"

### Stage 3 — Workshop
- Week label: "Week 2"
- Activity title: "Prioritisation workshop (2 hrs)"
- Bullets:
  - Map opportunities against {{client}}'s objectives
  - Score feasibility, effort, and ROI per opportunity
  - Agree go/no-go candidates for Assembly
- Output: "Prioritised roadmap ready for leadership decision"

### Source
Omit (this is our method).

### Source material in `client-wiki`
None — method is product-level.

### Writing rules reminders
- Each bullet one line, no full stops (not sentences)
- "Validated", "Scored", "Prioritised" — strong past participles in outputs

---

## Slide 6 — Risk reversal

### Slide type
`left-third-title` (section label "Guarantee" or "Our commitment")

### Variant
`bullets` with `numbered: false` — 2 teal-dot items. The first states the guarantee, the second explains why we can make it.

### Purpose
Put the commercial risk on us. This is the slide that moves pricing from "spend" to "bet".

### Action title pattern
*"If the Survey doesn't find at least 1 FTE in implementable value, you don't pay"*.

### Body content
Two bullets:
1. **The guarantee in plain terms** — what "implementable value" means and how it's measured.
2. **Why we can make this guarantee** — AI-powered research compresses what a traditional consultancy would take months to do into days, so the upside is large enough to stand behind.

### Section subtitle (left panel)
"Why the risk\nis on us, not you"

### Source
Omit.

### Source material in `client-wiki`
None — commercial term, identical across clients.

### Writing rules reminders
- Plain, direct language — no hedges
- Do not dilute the guarantee with caveats on the slide; keep qualifiers for the contract

---

## Slide 7 — What you get: deliverables package

### Slide type
`card-list`

### Purpose
Make the outputs of the Survey concrete, so the client can picture what lands on their desk.

### Action title pattern
*"You leave the Survey with three artefacts that make use cases easy to action or defend"*.

### Lead subtitle (optional)
*"Each designed to move straight into Assembly or internal execution"*.

### Card 1
- Title: "Implementation-ready use cases"
- Metric: "{{N}}–{{M}} use cases"
- Description: Each use case documented with workflow, tool suggestions, costing, projected savings, and priority score — ready to hand to Assembly or an internal team.
- Category: "Execution"

### Card 2
- Title: "Leadership deck"
- Metric: "1 deck"
- Description: Investor- and board-ready narrative explaining each approved use case, its ROI, and its fit to the wider AI strategy — built to get budget signed off.
- Category: "Approval"

### Card 3
- Title: "Interactive opportunity map"
- Metric: "Living artefact"
- Description: A searchable map of every opportunity identified, updated as scope evolves or new hypotheses arrive. The client retains access after the engagement ends.
- Category: "Reference"

### Source
Omit.

### Source material in `client-wiki`
None — product-level deliverables.

### Writing rules reminders
- Category tags are short — one or two words
- Descriptions concrete: who uses this, for what decision

---

## Slide 8 — Next steps

### Slide type
`left-third-title` (section label "Next steps")

### Variant
`bullets` with `numbered: true` — 3–4 numbered actions with short bold titles and continuation text.

### Purpose
A low-commitment close. Clear actions, no pricing.

### Action title pattern
*"Three interviews, one workshop, roadmap in {{N}} weeks"*.

### Body content
Numbered list (3–4 items), no full stops:
1. Book 3 × 30-minute interviews — sponsor, ops lead, key operator
2. Share {{list of relevant internal docs — SOPs, org chart, system list}}
3. Workshop within 2 weeks of interviews
4. Roadmap delivered within {{X}} working days of the workshop

### Section subtitle (left panel)
"Low-commitment ask\nto start the Survey"

### Source
Omit.

### Source material in `client-wiki`
- `clients/{name}/{name}.md` — Next Steps section, if already populated

### Writing rules reminders
- **No pricing on this slide** — pricing is a separate conversation
- Each action starts with a verb
- Timeframes must be specific (weeks, days) — not "soon" or "shortly"

---

## When building a deck for a specific client

1. Open `clients/{name}/{name}.md` (the hub) and read top to bottom.
2. Populate slides 1, 2, 4, 8 from client-specific wiki content (situation, objectives, opportunities, next steps).
3. Slides 3, 5, 6, 7 are product-level — reuse verbatim, only swap `{{client}}` mentions.
4. Draft Action Titles first (the Ghost Deck — see `deck-playbook.md`). Agree the horizontal flow before populating bodies.
5. Apply `writing-rules.md` to every line, then run the Pre-Flight and Toothbrush passes from `deck-playbook.md`.
