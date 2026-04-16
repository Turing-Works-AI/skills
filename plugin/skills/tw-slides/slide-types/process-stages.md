# Component: Process Stages Slide (`process-stages`)

A full-width content slide showing a phased process as a horizontal timeline. Features chevron headers for each stage, numbered badges, week labels, and paired activity/output boxes per column. Used for sprint plans, improvement programmes, and phased engagements.

---

## Build workflow

**No example `.pptx` exists for this slide type yet.** Use the `pptxgenjs` code template at the bottom of this file. (TODO: build a `process-stages-example.pptx` so this slide type can move to the duplication-from-template default like the others.)

After build, run the visual-QA loop from `anthropic-skills:pptx`.

---

## Slide properties

| Property | Value |
|----------|-------|
| Width | 10.0 in |
| Height | 5.625 in |
| Background | `#FFFFFF` |
| Aspect ratio | 16:9 |

---

## Layout structure

```
┌──────────────────────────────────────────────────────────┐
│              [To discuss]                                │  ← sticker
│                                                          │
│  Action title (bold, large, inherited theme style)       │
│  Subtitle (teal, smaller)                                │
│                                                          │
│  ┌─ chevron ─┐  ┌─ chevron ─┐  ┌─ chevron ─┐           │
│  │①Stage 1   │→ │②Stage 2   │→ │③Stage 3   │           │
│  └───────────┘  └───────────┘  └───────────┘           │
│    Week 1          Week 1-2        Week 2                │
│  ┌───────────┐  ┌───────────┐  ┌───────────┐           │
│  │ Activity   │  │ Activity   │  │ Activity   │           │
│  │ • bullet   │  │ • bullet   │  │ • bullet   │           │
│  │ • bullet   │  │ • bullet   │  │ • bullet   │           │
│  └───────────┘  └───────────┘  └───────────┘           │
│  ┌───────────┐  ┌───────────┐  ┌───────────┐           │
│  │ Output     │  │ Output     │  │ Output     │           │
│  │ text       │  │ text       │  │ text       │           │
│  └───────────┘  └───────────┘  └───────────┘           │
│                                                          │
│ 6.                                                       │
│ ████████████████ Bottom accent bar ██████████████████████ │
└──────────────────────────────────────────────────────────┘
```

---

## Key design decisions

- **Full-width layout** — no left panel. The title and subtitle sit directly on the white background, not inside a branded panel.
- **Square boxes** — activity and output boxes use sharp corners (no rounded rectangles). This was an explicit design choice.
- **Separate activity and output boxes** — each column has two distinct boxes stacked vertically: the larger activity box on top and a shorter output box below. Do not combine them into a single box.
- **Consistent box fill** — both activity and output boxes use Light Stone `#E8E8E4`. Do not use different fills to distinguish them; the teal "Output" label provides sufficient visual separation.
- **Chevron shapes** — stage headers use preset chevron geometry, not rectangles. The first/active stage uses Deep Teal `#0E425B`; subsequent stages use Steel Blue `#1F4C60`.
- **Title preserves slide theme** — the action title inherits from the slide master/placeholder. Do not apply explicit brand fonts or colours to it when editing an existing deck.

---

## Element inventory

| # | Element type | Name/role | x (in) | y (in) | w (in) | h (in) |
|---|-------------|-----------|--------|--------|--------|--------|
| 1 | Text box (placeholder) | Action title | 0.69 | 0.47 | 8.65 | 0.62 |
| 2 | Text box | Subtitle | 0.69 | 0.95 | 8.65 | 0.30 |
| 3 | Rectangle | Sticker ("To discuss") | 3.65 | 0.00 | 2.70 | 0.20 |
| 4 | Chevron | Stage 1 header | 1.13 | 1.37 | 2.53 | 0.73 |
| 5 | Chevron | Stage 2 header | 3.96 | 1.37 | 2.53 | 0.73 |
| 6 | Chevron | Stage 3 header | 6.80 | 1.37 | 2.69 | 0.73 |
| 7 | Ellipse | Number badge 1 | 1.31 | 1.51 | 0.40 | 0.40 |
| 8 | Ellipse | Number badge 2 | 4.15 | 1.51 | 0.40 | 0.40 |
| 9 | Ellipse | Number badge 3 | 6.98 | 1.51 | 0.40 | 0.40 |
| 10 | Text box | Week label 1 | 1.71 | 2.19 | 1.37 | 0.20 |
| 11 | Text box | Week label 2 | 4.55 | 2.19 | 1.37 | 0.20 |
| 12 | Text box | Week label 3 | 7.46 | 2.19 | 1.37 | 0.20 |
| 13 | Rectangle | Activity box 1 | 1.13 | 2.48 | 2.53 | 1.95 |
| 14 | Rectangle | Activity box 2 | 3.96 | 2.48 | 2.53 | 1.95 |
| 15 | Rectangle | Activity box 3 | 6.80 | 2.48 | 2.69 | 1.95 |
| 16 | Rectangle | Output box 1 | 1.13 | 4.55 | 2.53 | 0.75 |
| 17 | Rectangle | Output box 2 | 3.96 | 4.55 | 2.53 | 0.75 |
| 18 | Rectangle | Output box 3 | 6.80 | 4.55 | 2.69 | 0.75 |
| 19 | Rectangle | Bottom accent bar | 0.00 | 5.525 | 10.00 | 0.10 |

---

## Element details

### Element 1: Action title

| Property | Value |
|----------|-------|
| Shape | Placeholder / text box |
| Fill | None |
| Text | `{{action_title}}` — conclusion statement (e.g. "A process improvement sprint will identify root causes and implement fixes to improve target P2P metrics") |
| Style | **Inherited from slide master** — do not override |
| Notes | When editing an existing deck, preserve the original placeholder formatting |

### Element 2: Subtitle

| Property | Value |
|----------|-------|
| Shape | Text box |
| Fill | None |
| Text | `{{subtitle}}` (e.g. "Based on week 1 findings, several fixes can be initiated immediately") |
| Font | Inter Tight |
| Size | 12pt |
| Weight | Regular |
| Colour | `#518C94` (Teal) |
| Alignment | Left |

### Element 3: Sticker

| Property | Value |
|----------|-------|
| Shape | Rectangle |
| Fill | `#ADCFC9` (Aqua) |
| Border | None |
| Text | `{{sticker}}` (e.g. "For discussion", "To discuss") |
| Font | Inter Tight |
| Size | 10pt |
| Weight | Bold |
| Colour | `#0E425B` (Deep Teal) |
| Alignment | Centre |

### Elements 4–6: Chevron headers

| Property | Value |
|----------|-------|
| Shape | Chevron (preset geometry `chevron`) |
| Fill (active/first stage) | `#0E425B` (Deep Teal) |
| Fill (subsequent stages) | `#1F4C60` (Steel Blue) |
| Border | None |

**Text structure (multi-run):**

| Run | Content | Font | Size | Weight | Colour |
|-----|---------|------|------|--------|--------|
| 1 | `"Stage N \| "` | Inter Tight | 11pt | Bold | `#FFFFFF` |
| 2 | `{{stage_name}}` (e.g. "Diagnose") | Inter Tight | 11pt | Regular | `#FFFFFF` |

### Elements 7–9: Number badges

| Property | Value |
|----------|-------|
| Shape | Ellipse |
| Fill | `#FFFFFF` |
| Border | None |
| Text | `{{stage_number}}` (1, 2, 3) |
| Font | Inter Tight |
| Size | 16pt |
| Weight | Bold |
| Colour | `#0E425B` (Deep Teal) |
| Alignment | Centre |

### Elements 10–12: Week labels

| Property | Value |
|----------|-------|
| Shape | Text box (transparent) |
| Fill | None |
| Text | `{{week_label}}` (e.g. "Week 1", "Week 1-2") |
| Font | Inter Tight |
| Size | 11pt |
| Weight | Bold |
| Colour | `#518C94` (Teal) |
| Alignment | Centre |

### Elements 13–15: Activity boxes

| Property | Value |
|----------|-------|
| Shape | Rectangle (square corners) |
| Fill | `#E8E8E4` (Light Stone) |
| Border | None |
| Inner margin | 0.12 in all sides |
| Word wrap | Yes |

**Text structure:**

| Paragraph | Content | Font | Size | Weight | Colour | Spacing |
|-----------|---------|------|------|--------|--------|---------|
| Title | `{{activity_title}}` | Inter Tight | 11pt | Bold | `#072E45` | line 120% |
| Bullets | `"• {{bullet}}"` (one per paragraph) | Inter Tight | 11pt | Regular | `#3A3A3A` | line 125%, 5pt space before first bullet, 2pt between bullets |

### Elements 16–18: Output boxes

| Property | Value |
|----------|-------|
| Shape | Rectangle (square corners) |
| Fill | `#E8E8E4` (Light Stone) |
| Border | None |
| Inner margin | 0.12 in all sides |
| Word wrap | Yes |

**Text structure:**

| Paragraph | Content | Font | Size | Weight | Colour | Spacing |
|-----------|---------|------|------|--------|--------|---------|
| Label | `"Output"` | Inter Tight | 11pt | Bold | `#518C94` (Teal) | line 120% |
| Value | `{{output_text}}` | Inter Tight | 11pt | Regular | `#3A3A3A` | line 125%, 2pt space before |

### Element 19: Bottom accent bar

| Property | Value |
|----------|-------|
| Shape | Rectangle |
| Fill | `#518C94` (Teal) |
| Border | None |

---

## Computed constants

| Constant | Value | Notes |
|----------|-------|-------|
| Left margin | 1.13 in | Left edge of column 1 elements |
| Column 1 width | 2.53 in | Chevron, activity box, output box width |
| Column 2 left | 3.96 in | x of column 2 elements |
| Column 2 width | 2.53 in | |
| Column 3 left | 6.80 in | x of column 3 elements |
| Column 3 width | 2.69 in | Slightly wider to fill right margin |
| Column gap | ~0.30 in | Between columns 1-2 and 2-3 |
| Chevron top | 1.37 in | y of all chevrons |
| Chevron height | 0.73 in | |
| Activity box top | 2.48 in | y of activity boxes |
| Activity box height | 1.95 in | |
| Gap between boxes | 0.12 in | Between activity and output boxes |
| Output box top | 4.55 in | y of output boxes |
| Output box height | 0.75 in | |
| Bottom bar y | 5.525 in | |

---

## Template parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `action_title` | string | Yes | Conclusion statement for the slide |
| `subtitle` | string | No | Supporting context line below title, in teal |
| `sticker` | string | No | Status badge text (e.g. "For discussion") |
| `stages` | object[] | Yes | Array of stage objects (see below) |
| `slide_number` | number | No | Page number (displayed bottom-left if present) |

### Stage object

```yaml
stages:
  - number: 1
    name: "Diagnose"
    active: true            # Deep Teal fill; false = Steel Blue
    week_label: "Week 1"
    activity_title: "Problem-solving sessions"
    bullets:
      - "Whiteboard workshops with AP team to develop hypothesis on poor metric performance"
      - "Analysis of financial data to validate hypothesis"
    output: "Validated issue hypotheses"
  - number: 2
    name: "Plan"
    active: false
    week_label: "Week 1-2"
    activity_title: "Form hypotheses"
    bullets:
      - "Propose tool and workflow improvements to improve issue"
      - "Prioritise work plan by effort and expected metric improvement"
    output: "Prioritised improvement roadmap"
  - number: 3
    name: "Implement"
    active: false
    week_label: "Week 2"
    activity_title: "Implement changes"
    bullets:
      - "Configure tool and process changes (Zudello workflows, PO policy, approval workflows)"
      - "Set-up tracking of target KPIs"
    output: "Implemented tool and workflow fixes"
```

---

## Scaling notes

This component is designed for 3 stages. To adapt:

- **2 stages**: widen columns to fill the space; keep same vertical layout
- **4+ stages**: reduce column widths proportionally; consider reducing chevron text to 10pt; activity box text must never go below 11pt
