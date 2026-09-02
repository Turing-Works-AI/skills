# Component: Numbered Card List (`card-list`)

A full-width content slide presenting numbered items as stacked horizontal cards. Each card has a number badge, a title row (issue name + metric), a body description, and a category tag. No left branded panel — content spans the full slide width.

Use for: issue lists, risk registers, opportunity catalogues, prioritised findings — any content where N items (typically 3–6) each need a title, a key metric, a short description, and a category label.

---

## Build workflow

**No example `.pptx` exists for this slide type yet.** Use the `pptxgenjs` code template at the bottom of this file. (TODO: build a `card-list-example.pptx` so this slide type can move to the duplication-from-template default like the others.)

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
│            [ To discuss ]                    [Page badge] │
│                                                          │
│  Action title (large, SemiBold, ink)                     │
│  Lead subtitle (blue-grey, optional)                     │
│                                                          │
│  ┌─────────────────────────────────────────────────────┐ │
│  │ (1)  Issue title          Metric     [ Category ]   │ │
│  │      Description text spanning full card width      │ │
│  └─────────────────────────────────────────────────────┘ │
│  ┌─────────────────────────────────────────────────────┐ │
│  │ (2)  Issue title          Metric     [ Category ]   │ │
│  │      Description text spanning full card width      │ │
│  └─────────────────────────────────────────────────────┘ │
│  ...                                                     │
│  Source: ...                                             │
├──────────────────────────────────────────────────────────┤
│ ████████████████ Bottom accent bar ██████████████████████ │
└──────────────────────────────────────────────────────────┘
```

---

## Design decisions (March 2026)

These choices were made during the Lyka AP engagement and represent Alasdair's preferred treatment for this slide type.

1. **Title treatment**: Large SemiBold (~24pt) ink `#1B3A5C` — significantly larger than the 12pt action titles used on left-panel situation slides. This slide type leads with impact, not a section label.
2. **Issue title and metric are separated by whitespace**, not concatenated with an em dash. The title sits left; the metric sits to its right with a clear gap. This creates a scannable two-column effect on the title row.
3. **Category tags are vertically centred** on the right edge of each card, not placed at the top-right corner.
4. **Number badges are vertically centred** within the card, not top-aligned.
5. **Lead subtitle** (blue-grey `#5C7189`, ~14pt) appears below the action title when the slide has a supporting statement. Omit when not needed.
6. **Sticker uses the existing deck sticker style** (light blue `#BFD3E6` fill) — not the Guide accent colour.

---

## Grid constants

| Constant | Value | Notes |
|----------|-------|-------|
| Content left edge | 0.7 in | Left margin for title and cards |
| Content right edge | 9.3 in | |
| Content width | 8.6 in | Full card width |
| Title y | 0.55 in | Top of action title |
| Lead subtitle y | Title bottom + 0.05 in | Below title, when present |
| Cards start y | ~1.2 in | Below title/subtitle + gap |
| Card height | 0.85–0.95 in | Adjust to fit 5 cards above source line |
| Card gap | 0.06 in | Between cards |
| Card corner radius | adj = 12000 | Subtle rounding |

---

## Element details

### Action title

| Property | Value |
|----------|-------|
| Position | x: 0.7 in, y: 0.55 in |
| Size | w: 8.6 in, h: auto (1–2 lines) |
| Font | Plus Jakarta Sans |
| Size | 24pt |
| Weight | Bold |
| Colour | `#1B3A5C` (Ink) |
| Alignment | Left |
| Line spacing | 115% |

### Lead subtitle (optional)

| Property | Value |
|----------|-------|
| Position | x: 0.7 in, y: below title |
| Font | Plus Jakarta Sans |
| Size | 14pt |
| Weight | Regular |
| Colour | `#5C7189` (Blue-grey) |
| Alignment | Left |

### Card background

| Property | Value |
|----------|-------|
| Shape | Rounded rectangle |
| Fill | `#FFFFFF` (White) |
| Border | None |
| Corner radius | adj = 12000 |

### Number badge

| Property | Value |
|----------|-------|
| Shape | Ellipse |
| Size | 0.34 × 0.34 in |
| Fill | `#1B3A5C` (Ink) |
| Vertical position | Centred within card height |
| Horizontal position | 0.15 in from card left edge |
| Text | Plus Jakarta Sans, 11pt, Bold, `#FFFFFF`, Centre |

### Title row

Two text elements on the same horizontal line, to the right of the badge:

**Issue title:**

| Property | Value |
|----------|-------|
| Position | 0.6 in from card left edge |
| Font | Plus Jakarta Sans |
| Size | 12pt |
| Weight | Bold |
| Colour | `#1B3A5C` (Ink) |
| Vertical position | ~0.08 in from card top |

**Metric:**

| Property | Value |
|----------|-------|
| Position | Right of issue title, separated by whitespace (~0.3 in gap or tab) |
| Font | Plus Jakarta Sans |
| Size | 12pt |
| Weight | Regular |
| Colour | `#5C7189` (Blue-grey) |

The title and metric sit on the same baseline. Keep the metric visually distinct through colour alone — no separator character (no em dash, no pipe).

### Description

| Property | Value |
|----------|-------|
| Position | Below title row, 0.6 in from card left edge |
| Width | Card width − 0.75 in (full width below title, ignoring tag) |
| Font | Plus Jakarta Sans |
| Size | 10pt |
| Weight | Regular |
| Colour | `#1B3A5C` (Body) |
| Line spacing | 125% |

### Category tag

| Property | Value |
|----------|-------|
| Shape | Rounded rectangle pill |
| Fill | `#FFFFFF` (White) with visible border `#BFD3E6` (Guide), 0.75pt |
| Size | ~1.5 × 0.24 in |
| Corner radius | adj = 16000 |
| Position | Right edge of card (0.15 in inset), **vertically centred** within card |
| Text | Plus Jakarta Sans, 10pt, Italic, `#5C7189` (Blue-grey), Centre |

### Sticker ("To discuss" / status)

| Property | Value |
|----------|-------|
| Position | Centred horizontally at top of slide, y ≈ -0.01 in (peeking in) |
| Size | ~2.7 × 0.2 in |
| Fill | `#BFD3E6` (Guide — matches existing deck sticker) |
| Border | 0.75pt `#1B3A5C` |
| Text | Plus Jakarta Sans Light, 12pt, `#1B3A5C`, Centre |

### Source citation

| Property | Value |
|----------|-------|
| Position | x: 0.7 in, y: 5.08 in |
| Size | w: 8.6 in, h: 0.25 in |
| Font | Plus Jakarta Sans |
| Size | 8pt |
| Weight | Regular |
| Style | Italic |
| Colour | `#5C7189` (Blue-grey) |

### Corner triangle + page badge

Per global constants (see `../brand.md`).

### Bottom accent bar

Per global constants (see `../brand.md`).

---

## Template parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `action_title` | string | Yes | Main slide heading (conclusion statement) |
| `lead` | string | No | Blue-grey subtitle below the action title |
| `sticker` | string | No | Status badge (e.g. "To discuss", "Preliminary") |
| `cards` | object[] | Yes | Array of card objects (see below) |
| `source` | string | No | Source citation |
| `slide_number` | number | Yes | Page number |

### Card object

```yaml
cards:
  - title: "Issue or item name"
    metric: "Key number or KPI"
    description: "One or two sentences explaining the issue and its impact"
    category: "Dashboard or category label"
```

---

## Capacity

- **5 cards** fit comfortably with a 2-line title and source line
- **6 cards** possible if the title is single-line and card height is reduced to ~0.72 in
- **3–4 cards** allow more generous card height (~1.1 in) for longer descriptions
- Beyond 6 items, split across two slides or use a table component instead
