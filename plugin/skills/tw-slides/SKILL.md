---
name: tw-slides
description: Master skill for creating, editing, or reviewing Turing Works slide decks and client presentations. Combines Turing Works brand standards (colours, typography, layouts) with consulting-grade slide craft (MBB structure, action titles, vertical/horizontal flow, MECE reasoning). Use this skill whenever Alasdair asks to create a Turing Works presentation, client proposal, pitch deck, workshop deck, or any branded output. Also trigger when the user says "make it on-brand", "use our brand colours", "Turing Works style", "ghost deck", "action title", or references building slides for a client. This skill supersedes all generic design and slide defaults — always consult it before generating branded content.
---

# TW Slides — Turing Works Slide Craft & Brand Skill

This skill governs all Turing Works slide creation. It combines two things:
1. **Brand standards** — canonical colours, typography, and layout patterns derived from the approved EcoOutdoor proposal (Feb 2026)
2. **Slide craft** — MBB-standard content structure, writing discipline, and flow principles

Read both sections before building any deck. The brand section tells you *how it should look*. The craft section tells you *what it should say and how to structure it*.

---

## SKILL STRUCTURE

This skill spans multiple files. Read the relevant ones before building a slide.

```
tw-slides/
├── SKILL.md              ← You are here. Top-level brand + craft rules.
├── constants.md           ← Shared visual constants (colours, typography, grid)
│
├── content/               ← WHAT to write on each slide type
│   ├── situation.md       ← Action title patterns, body structure, bold rules
│   ├── objectives.md      ← Focus area structure, subtitle formula
│   └── workplan.md        ← Verb progression, deliverables, cell bullets
│
├── components/            ← HOW each slide looks (positions, shapes, code)
│   ├── situation/spec.md  ← Branded left panel + right content area
│   ├── objectives/spec.md ← Left panel + combined title/body text box
│   ├── workplan/spec.md   ← Week × workstream matrix grid
│   └── table-3col/spec.md ← Generic 3-column table with summary row
│
└── templates/
    └── brief-template.yaml ← Copy-paste YAML briefing format
```

**When building a specific slide type:**
1. Read this file (SKILL.md) for universal brand and craft rules
2. Read the relevant `content/*.md` for what to write
3. Read the relevant `components/*/spec.md` for exact visual placement
4. Reference `constants.md` for shared values

---

## WORKING MODE: ONE SLIDE AT A TIME

Slides are built and edited individually, not as a full deck in one pass. Before starting any slide, orient yourself:

### Step 1 — Establish context
- **Where does this slide sit in the deck?** Identify its section (title / exec summary / content / recommendation / appendix) and its role in the horizontal narrative flow.
- **What is the goal of this slide?** What single conclusion should a reader take away?
- If this is unclear, ask before proceeding.

### Step 2 — Read all inputs before touching content
Inputs arrive in layers — read all of them before writing anything:

| Input | What it contains | Priority |
|-------|-----------------|----------|
| **Yellow stickies** | Explicit edit instructions from Alasdair — specific changes, corrections, or directions for this slide | **Highest** — follow these literally unless they conflict with brand rules |
| **Provisional slide content** | Existing text, labels, and structure already on the slide — treat as raw material to be formatted, edited, and completed, not discarded | **High** — preserve intent, upgrade execution |
| **Meeting transcript** | Source of truth for facts, numbers, client language, and context — mine this for content that belongs on the slide | **High** — extract, don't invent |
| **User instructions** | Any additional direction given in the conversation | **High** — apply alongside sticky notes |

### Step 3 — Resolve conflicts
- Sticky note overrides provisional content when they directly contradict
- Meeting transcript provides evidence for what the content *should* say
- Brand standards govern *how* anything looks — these are never overridden by sticky notes
- If a sticky note asks for something off-brand (e.g. wrong colour, wrong font), apply the brand-compliant equivalent and flag the deviation

### Step 4 — Build the slide
- Apply the appropriate layout pattern from Part 1
- Write the Action Title as a conclusion (5–6 words), not a topic label
- Structure body content MECE — no clotheslines
- Include source line if any data is present
- Apply slide number badge if this is a content slide

### Step 5 — State your assumptions
After delivering the slide, briefly note:
- What you inferred from the transcript (if anything)
- Any content gaps where the transcript/stickies didn't provide enough detail (flag for Alasdair to fill)
- Any brand or craft decisions worth flagging

---

## PART 1: BRAND STANDARDS

### Colour Palette

#### Primary (Dark Blues) — backgrounds, headers, section titles
| Name | Hex | Usage |
|------|-----|-------|
| Midnight Navy | `#072E45` | Title slide backgrounds, dark section backgrounds |
| Deep Teal | `#0E425B` | Primary brand colour; headers, key shapes |
| Ocean | `#0A3851` | Supporting dark elements |
| Steel Blue | `#1F4C60` | Secondary dark backgrounds |
| Slate | `#134F68` | Alternate header fill |

#### Secondary (Warm Neutrals) — slide backgrounds, cards, off-white areas
| Name | Hex | Usage |
|------|-----|-------|
| Sand | `#B8AD90` | Subtle accent, dividers |
| Cream | `#F7EACC` | Light backgrounds, card fills |
| Off-White | `#F9F9F7` | Slide body background (default) |
| Light Stone | `#E8E8E4` | Alternate card/panel fill |

#### Accent (Teal/Aqua) — highlights, icons, callouts — use sparingly
| Name | Hex | Usage |
|------|-----|-------|
| Aqua | `#ADCFC9` | Icon circles, accent borders, callout blocks |
| Teal | `#518C94` | Supporting accent, icon fills, section markers |
| Warm Tan | `#CEC3A1` | Tertiary neutral |

#### Text Colours
| Context | Hex |
|---------|-----|
| Body text on light BG | `#3A3A3A` |
| Body text on dark BG | `#FFFFFF` |
| Headings on dark BG | `#FFFFFF` |
| Headings on light BG | `#072E45` or `#0E425B` |
| Muted / source / caption text | `#518C94` or `#B8AD90` |

#### Structural Colour Rule ("Sandwich")
- **Title slide**: Dark (`#072E45`) — white and cream text
- **Content slides**: Light (`#F9F9F7` or white) — dark text, teal accents
- **CTA / section divider slides**: Dark (`#0D425C`) — white text, aqua accents
- **Closing slide**: Dark background, white text

---

### Typography

**Primary font: Inter Tight** (all weights)
**Fallback: Calibri** — never default to Arial for body text; never use Trebuchet MS.

#### Font Size Scale

| Element | Size (pt) | Weight | Colour |
|---------|-----------|--------|--------|
| Hero/display title (cover) | 52pt | Bold | `#FFFFFF` or `#F7EACC` |
| Slide main title (Action Title) | 16pt | Bold | `#FFFFFF` (dark BG) / `#072E45` (light BG) |
| Section header / subtitle (Lead) | 18pt | SemiBold | `#0E425B` or `#FFFFFF` |
| Body / content text | 11–12pt | Regular | `#3A3A3A` |
| Supporting body / sub-bullets | 10pt | Regular | `#3A3A3A` |
| Labels / captions / source lines | 10pt | Regular | `#518C94` or `#B8AD90` |

*In pptxgenjs, multiply pt by 100: 16pt → `fontSize: 1600`. Minimum font size on any slide is 10pt — no text may go below this.*

#### Typography Rules
- Set Inter Tight explicitly on every text box — never rely on theme defaults
- Titles left-aligned on content slides; centred only on cover/thanks slides
- Source lines ("Source: …") always at bottom of slide, 10pt, muted teal
- Numbered callout badges: bold white text on dark teal circle background
- No italic for body text; reserve for taglines or pull-quotes only

---

### Layout Patterns

#### Cover / Title Slide
- Full dark background: `#072E45`
- Client logo + Turing Works wordmark top-left, separated by `×` in cream
- Hero title: 52pt bold white, left-aligned, upper-left quadrant
- Sub-tagline: 14–16pt, cream (`#F7EACC`), below title
- Date + "Confidential" footer: 11pt, `#ADCFC9`, bottom-left

#### Standard Content Slide
- Background: white or `#F9F9F7`
- Slide number badge: dark teal circle, top-right (white number inside)
- Section label: small sentence-case label in teal above main heading (e.g. "Situation", "Proposal")
- Action Title: 16pt bold `#072E45`, top-left — the key message of the slide
- Lead (optional): 11–12pt dark teal, right column or below heading — supplementary context
- Body content: 10–12pt, `#3A3A3A`
- Source line: 10pt `#518C94`, bottom of slide

#### Two-Column Layout
- Left column: text/headings/numbered steps (~55% width)
- Right column: supporting context, icons, or illustrative text (~40% width)
- Use `#ADCFC9` or `#518C94` for icon circles alongside text rows

#### Card/Grid Layout
- 2×2 grid of cards with light fill (`#F9F9F7` or `#E8E8E4`)
- Each card: numbered badge (dark teal), bold short title (14pt), body text (10pt)
- Uniform card padding; consistent border radius (4–6pt)

#### Dark CTA / Section Divider Slide
- Background: `#0D425C` or `#072E45`
- Title: 27pt bold white, left-aligned
- Bullets: 14–16pt white, with `#ADCFC9` markers
- No source line needed

#### Bio / Profile Slide
- White background; circular headshot top-left
- Name: 18pt bold `#072E45`; Title: 12pt `#518C94`
- Summary: 10pt `#3A3A3A`; Experience bullets: 10pt `#3A3A3A`

---

### Shape & Decoration Rules
- **Numbered badges**: Dark teal circles (`#0E425B`) with white bold numbers
- **Icon circles**: `#ADCFC9` or `#518C94` fill, white icon inside
- **No underline accents beneath titles** — use background contrast or whitespace instead
- **Divider lines**: sparingly; `#ADCFC9` at 0.5–1pt
- **No drop shadows or outer glows** — flat and clean only
- **Callout bubbles**: aqua or cream fill, small border, used to annotate charts

---

## PART 2: SLIDE CRAFT (MBB-STANDARD)

### Deck Structure

Every Turing Works client deck follows this five-section spine:

| # | Section | Purpose |
|---|---------|---------|
| 1 | **Title page** | States the deck's purpose — title (<10 words), sub-tagline, client/TW branding, date |
| 2 | **Executive summary** ("At a glance") | Summarises the full story in one slide — key insights across all themes; the most important slide and hardest to write |
| 3 | **Contents and exhibits** | The analytical core — all quantitative and qualitative evidence supporting the argument |
| 4 | **Recommendations / Next steps** | Conclusion with specific actions; every recommendation must show its outcome/impact |
| 5 | **Appendix** (optional) | Backup data, process detail, methodology — keeps the main deck clean |

The executive summary should be writable as a standalone document. If a reader only reads one slide, it should be this one.

---

### Anatomy of a Single Slide

Every content slide has three zones:

**Top — Action Title + Lead**
- **Action Title**: 5–6 words, the key takeaway of this slide stated as a conclusion, not a topic. Bad: "Market size". Good: "ANZ e-commerce market growing at 18% CAGR through 2027".
- **Lead** (optional): 10-word elaboration below the Action Title — adds units, context, or a qualifying clause.
- Sticker (optional, top-right): "For Discussion", "Preliminary", "Indicative", or "Illustrative" — signals the status of data on this slide.

**Middle — Chart or Exhibit**
- Quantitative content — chart (see chart types below)
- Qualitative content — diagram, process map, 2×2, or structured text layout
- Every chart needs: a sub-title with measurement units, a legend, and optionally callout bubbles for annotations not visible in the data

**Bottom — Supporting information**
- **Footnotes**: clarifications for specific data points (numbered superscripts)
- **Source citation**: always present if data is external — "Source: [origin]" — bottom-left
- **Page number**: bottom-right, inside a dark teal badge

---

### Chart Type Selection

| Data type | Chart family |
|-----------|--------------|
| Comparison over time | Line chart |
| Ranking / comparison across categories | Bar / column |
| Part-to-whole | Percentage / stacked bar / pie (use sparingly) |
| Variance / bridge | Waterfall |
| Distribution / correlation | Scatter plot |
| Market segmentation | Mekko / Marimekko |

Always annotate the most important data point with a callout bubble. Never leave a chart to speak for itself.

---

### Content Flow

#### Vertical Flow (within each slide)
Each slide argues one point. Structure it as:
1. **Key message** — Action Title (what is the conclusion?)
2. **Main arguments** — section headers or lead bullets (why?)
3. **Sub-arguments + data** — chart or supporting text (prove it)

Apply the **Pyramid Principle**: state the answer first, then support it with arguments, then support each argument with data. Never bury the conclusion.

Apply **MECE** discipline: arguments must be mutually exclusive (no overlap) and collectively exhaustive (no gaps). Avoid "clotheslines" — long undifferentiated bullet lists with no structure. Group bullets into 3–4 named categories.

#### Horizontal Flow (across the whole deck)
Read the Action Titles of every slide in sequence — they should tell a coherent story without the body of each slide. If the titles don't chain into a narrative, the deck's storyline is broken.

Use a **Ghost Deck** to plan this before building:
- Draft only titles and headlines on blank slides
- Sketch rough exhibit shapes (no real data yet)
- Agree the storyline with the client/team before populating
- Revise until the horizontal title-to-title flow makes sense

---

### Writing Rules

1. **Top-down always**: state the conclusion before the evidence, not after
2. **Action titles, not topic labels**: every title must be a statement with a verb and a direction
3. **Concise and professional**: no filler phrases; every word earns its place
4. **Data-supported**: every assertion needs evidence — chart, statistic, case study, or named source
5. **Units and sources on every chart**: no exceptions; source cited at slide bottom
6. **No clotheslines**: bullet lists must be grouped and structured, not enumerated randomly
7. **Bold to highlight**: use sparingly to draw the eye to the single most important phrase per text block

---

### Language & Tone

- **Sentence case** for all headings and Action Titles (not Title Case)
- **Direct and active**: "Turing Works will deliver…" not "It is proposed that delivery will occur…"
- **Specific over vague**: name tools, methods, timelines, and numbers wherever possible
- **Result-oriented**: every recommendation states its expected outcome
- **Confident but not salesy**: no "best-in-class", "world-leading", "game-changer"
- **Source attribution**: "Source: …" on any slide making a factual claim
- No LLM-isms: no "ship it", "delve into", "leverage" (unless quoting client language), "revolutionary"
- Em dash (—) not double hyphen (--)
- Months written in full in formal context: "February 2026" not "Feb 2026"

---

### Slide Structure Conventions

- **Slide number**: top-right corner badge on all content slides; hidden on cover and thanks
- **Section label**: short contextual anchor above or beside the Action Title (e.g. "Situation", "Objectives", "Terms")
- **Source line**: bottom of slide, always present if any claim or data is referenced
- **Appendix**: labelled divider slide in dark style, then backup slides follow
- **Closing slide**: "Thanks!" or "Next steps", dark background, white text

---

## Pre-Flight Checklist

Run through this before finalising any deck:

**Brand**
- [ ] All text boxes use Inter Tight explicitly
- [ ] Title slide: dark `#072E45` background
- [ ] Content slides: `#F9F9F7` or white background
- [ ] CTA/divider slides: dark teal background
- [ ] Slide number badges on all content slides
- [ ] No underline accents beneath titles
- [ ] Colours from palette only — no off-brand defaults

**Content**
- [ ] Executive summary slide present and self-contained
- [ ] Every Action Title is a conclusion, not a topic label
- [ ] Horizontal flow: titles chain into a coherent narrative
- [ ] Every chart has units, legend, and source citation
- [ ] No clothesline bullet lists — all grouped MECE
- [ ] All recommendations state their expected outcome
- [ ] Appendix contains backup; main deck is clean

**Language**
- [ ] Sentence case headings throughout
- [ ] Direct, active, specific language — no filler
- [ ] Source lines on all claim slides
- [ ] Passes tone check: confident, not salesy
