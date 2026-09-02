# TW Slides — Content Patterns

Content patterns for the **AI Survey** pitch deck. This is the generic, product-level template. When building a deck for a specific client, source the facts from that client's folder in the `client-wiki` repo (`clients/{name}/`) and fill them into the patterns below.

For every slide: follow the pattern, render on the named slide type (see `slide-types/`), and apply `writing-rules.md` to every line.

---

## Deck spine

| # | Slide | Slide type | Variant |
|---|-------|------------|---------|
| 1 | Situation | `left-third-title` | `columns` (default) or `bullets` |
| 2 | Objectives | `left-third-title` | `bullets` (numbered) |

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
- No solution language on this slide — keep it focused on the client's current state

---

## Slide 2 — Objectives

### Slide type
`left-third-title`

### Variant
`bullets` with `numbered: true` — numbered ink circles, each with a SemiBold title and a continuation sentence. Numbered (not dotted) because objectives are a discrete, finite set the sponsor can count off.

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

## When building a deck for a specific client

1. Open `clients/{name}/{name}.md` (the hub) and read top to bottom.
2. Populate slides 1 and 2 from client-specific wiki content (situation, objectives).
3. Draft Action Titles first (the Ghost Deck — see `deck-playbook.md`). Agree the horizontal flow before populating bodies.
4. Apply `writing-rules.md` to every line, then run the Pre-Flight and Toothbrush passes from `deck-playbook.md`.
