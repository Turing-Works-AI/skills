# TW Slides — Brand Standards

Canonical visual standards for Turing Works decks: colours, typography, layout patterns, shape rules, and shared numerical constants. This file tells you *how a slide should look*. See `writing-rules.md` for *what it should say* and `deck-playbook.md` for *how to approach the deck as a whole*.

---

## Slide dimensions

| Property | Value |
|----------|-------|
| Width | 10.0 in |
| Height | 5.625 in |
| Aspect ratio | 16:9 |

---

## Colour palette

Six colours. The identity is a technical drawing checked with a red pen: ink on
white, faint construction lines showing, one red mark where two things meet.
Full rationale and the non-deck rules live in the `turing-works-brand` skill —
this file is the deck-specific application of it, not a second palette.

| Role | Name | Hex | Job on a slide |
|------|------|-----|----------------|
| Ink | Blueprint blue | `#1B3A5C` | All type, rules, chart lines, the mark. Also the background of cover and section slides |
| Surface | White | `#FFFFFF` | **The default slide background.** Use it as much as possible |
| Pen | Vermilion | `#D9432A` | The one thing on the slide to look at — the reconciled number, the delta that matters. Never a fill |
| Guide | Pale blueprint | `#BFD3E6` | Gridlines, baselines, dividers, table rules, card borders on ink. Never carries meaning |
| Muted | Blue-grey | `#5C7189` | Source lines, captions, axis labels, table headers, secondary text |
| Paper | Warm off-white | `#F4F1EA` | **Not for decks.** Large-format physical print only |

### Text colours

| Context | Hex |
|---------|-----|
| Body text on white | `#1B3A5C` (ink) |
| Secondary / caption / source on white | `#5C7189` (muted) |
| Body text on ink | `#FFFFFF` |
| Secondary text on ink | `#BFD3E6` (guide) |
| Headings on white | `#1B3A5C` (ink) |
| Headings on ink | `#FFFFFF` |
| The single emphasis on a slide | `#D9432A` (pen) |

### Rules

1. **White is the slide background. Use it as much as possible.** If you are
   unsure what a slide's background should be, it is white.
2. **Vermilion appears at most once per slide.** Never a background, never a
   shape fill, never a badge, never a state colour. If it is on two things, one
   of them is wrong. A slide with nothing worth pointing at has no vermilion.
3. **Guide lines are visible somewhere on every slide** — a baseline under the
   action title, a rule above the source line, chart gridlines. A slide with no
   guides has forgotten what the brand is.
4. **No black.** The ink is blue. If something needs to be darker, make it
   smaller or move it.
5. **No tinted panels or grey fills.** Cards and panels are white with a 0.8pt
   ink border. Contrast comes from the border and from whitespace, not from a
   change of surface.
6. **No green, no purple, no orange, no gradients, no drop shadows.**

### Prohibited

- **Orange — never.** Vermilion `#D9432A` is not orange and is not a substitute
  for one; it is reserved for the single emphasis described above.
- **The retired teal/cream palette.** `#072E45`, `#0E425B`, `#0A3851`, `#1F4C60`,
  `#134F68`, `#0D425C`, `#518C94`, `#ADCFC9`, `#B8AD90`, `#CEC3A1`, `#F7EACC`,
  `#F9F9F7`, `#E8E8E4`, `#F0F7F5`, `#BBD6EE` are no longer Turing Works colours.
  If you find them in a deck, it predates this standard — restate it.
- Any colour not in the palette table above.

### Structural Colour Rule ("Sandwich")

The rhythm survives; the colours change. Dark means ink, not navy.

- **Title slide**: ink `#1B3A5C` — white type, guide-coloured footer
- **Content slides**: white — ink type, guide lines, one vermilion at most
- **Section divider / CTA slides**: ink `#1B3A5C` — white type, guide markers
- **Closing slide**: ink background, white type

Content slides are the overwhelming majority of any deck, so the deck reads as
white with occasional ink breaks — not as a dark deck.

---

## Typography

### Font stack

| Priority | Font | Usage |
|----------|------|-------|
| Primary | Plus Jakarta Sans | All text — set explicitly on every text box |
| Fallback | Calibri | System fallback only, if Plus Jakarta Sans is unavailable |
| Never use | Inter Tight, Arial, Trebuchet MS, any serif, any mono | — |

Plus Jakarta Sans is a Google font: native in Google Slides, free to install and
embed in PowerPoint on Mac and Windows. Embed it when sending a .pptx.

**Two weights only: Regular (400) and SemiBold (600).** There is no Bold in this
identity. Where an old deck used Bold, use SemiBold.

### Font size scale

| Element | Size (pt) | Weight | Colour | Notes |
|---------|-----------|--------|--------|-------|
| Hero/display title (cover) | 52 | SemiBold | `#FFFFFF` | Cover slide only, on ink |
| Section title (left panel) | 28 | SemiBold | `#FFFFFF` | On ink background |
| Section header / subtitle | 18 | SemiBold | `#1B3A5C` / `#FFFFFF` | |
| Slide main title (Action Title) | 16 | SemiBold | `#1B3A5C` (white BG) / `#FFFFFF` (ink BG) | |
| Action title (content-1col variant) | 12 | SemiBold | `#1B3A5C` | Ink on white |
| Body / content text | 11–12 | Regular | `#1B3A5C` | |
| Section subtitle (left panel) | 10.5 | Regular | `#BFD3E6` | On ink background |
| Supporting body / sub-bullets | 10 | Regular | `#1B3A5C` | Minimum font size |
| Labels / captions / source lines | 7.5–10 | Regular | `#5C7189` | |

In pptxgenjs, multiply pt by 100: 16pt → `fontSize: 1600`. Minimum font size on
any slide is 10pt — no text may go below this.

### Numbers

Every number column is right-aligned. PowerPoint and Google Slides use the
font's default figures, so check that `1111` sets as wide as `8888`; if a column
does not line up, right-align it and adjust tracking rather than switching font.
Never set numbers in a mono — it is the same family throughout.

### Line spacing

| Element | Value |
|---------|-------|
| Section subtitle | 130% |
| Action title | 130% |
| Body content | 135% |

### Typography rules

- Set Plus Jakarta Sans explicitly on every text box — never rely on theme defaults
- Regular and SemiBold only; no Bold, no Light, no italic weights from the family
- Titles left-aligned on content slides; centred only on cover/thanks slides
- Sentence case throughout. Full stops on action titles
- Source lines ("Source: …") always at bottom of slide, 10pt, muted blue-grey
- Numbered callout badges: white SemiBold numerals on an ink circle
- No italic for body text; reserve for taglines or pull-quotes only

---

## Layout patterns

### Cover / title slide

- Full ink background: `#1B3A5C`
- Client logo + Turing Works wordmark top-left, separated by `×` in white
- Hero title: 52pt SemiBold white, left-aligned, upper-left quadrant
- Sub-tagline: 14–16pt Regular white, below title
- A single pale-blueprint guide line under the wordmark, 0.7pt `#BFD3E6`
- Date + "Confidential" footer: 11pt `#BFD3E6`, bottom-left

### Standard content slide

- Background: white `#FFFFFF`
- Slide number badge: ink circle, top-right, white numeral inside
- Section label: small sentence-case label in blue-grey `#5C7189` above the main heading (e.g. "Situation", "Proposal")
- Action Title: 16pt SemiBold ink `#1B3A5C`, top-left — the key message of the slide
- Guide rule: 0.7pt `#BFD3E6` directly under the action title, full content width
- Lead (optional): 11–12pt blue-grey, right column or below heading — supplementary context
- Body content: 10–12pt Regular ink `#1B3A5C`
- At most one vermilion `#D9432A` element — the number the slide is actually about
- Source line: 10pt `#5C7189`, bottom of slide

### Two-column layout

- Left column: text/headings/numbered steps (~55% width)
- Right column: supporting context, icons, or illustrative text (~40% width)
- Icon circles alongside text rows: 0.8pt ink outline, white fill, ink glyph — outlined, not filled

### Card/grid layout

- 2×2 grid of cards: white fill, 0.8pt ink border `#1B3A5C`, 4–6pt radius
- Each card: numbered ink badge, SemiBold short title (14pt), body text (10pt)
- Uniform card padding; no tinted fills, no shadows

### Numbered card list (full-width)

- Full-width slide (no left panel); white background
- Action title: **24pt SemiBold ink** — larger than standard content slides, leads with impact
- Optional blue-grey lead subtitle (14pt) below the title
- 3–6 stacked horizontal cards: white fill, 0.8pt ink border, rounded corners
- Each card: numbered ink badge (vertically centred), **issue title** (SemiBold ink) and **metric** (blue-grey, or vermilion on the one card that matters most) on the same line separated by whitespace (not em dash or pipe), description text below spanning full width, category tag pill (0.8pt guide border, blue-grey text) vertically centred on right edge
- Use for: issue lists, findings, risk registers, prioritised items
- Full spec: `slide-types/card-list.md`

### Ink CTA / section divider slide

- Background: ink `#1B3A5C`
- Title: 27pt SemiBold white, left-aligned
- Bullets: 14–16pt white, with `#BFD3E6` markers
- No source line needed

### Bio / profile slide

- White background; circular headshot top-left, 0.8pt ink ring
- Name: 18pt SemiBold `#1B3A5C`; Title: 12pt `#5C7189`
- Summary: 10pt `#1B3A5C`; Experience bullets: 10pt `#1B3A5C`

### Reconciliation chart

The signature Turing Works chart, and the one to reach for on any case study or
results slide. Two or more lines from different sources — solid for the primary,
dashed for the others — on pale-blueprint gridlines, with a single vermilion
point where the sources agree, labelled "reconciled".

- Gridlines: 0.7pt `#BFD3E6`; no chart border, no legend box
- Lines: ink `#1B3A5C`, 1.6pt; label the lines directly, not in a legend
- Axis labels: 10–11pt `#5C7189`
- The reconciled point is the slide's one vermilion element

---

## Shape & decoration rules

- **Numbered badges**: ink circles (`#1B3A5C`) with white SemiBold numerals
- **Icon circles**: 0.8pt ink outline, white fill, ink glyph — never a filled disc
- **No underline accents beneath titles** — use a guide rule or whitespace instead
- **Divider and rule lines**: `#BFD3E6` at 0.5–0.7pt
- **Guide lines are visible on every slide** — a rule under the action title counts
- **No drop shadows, outer glows, gradients or tinted panels** — flat, white, and ruled
- **Callout annotations**: 0.8pt ink border on white, no fill; the pointer line in guide colour

---

## Slide structure conventions

- **Slide number**: top-right corner badge on all content slides; hidden on cover and thanks
- **Section label**: short contextual anchor above or beside the Action Title (e.g. "Situation", "Objectives", "Terms")
- **Source line**: bottom of slide, always present if any claim or data is referenced
- **Appendix**: labelled divider slide in ink style, then backup slides follow
- **Closing slide**: "Thanks!" or "Next steps", ink background, white text

---

## Grid constants

| Constant | Value | Notes |
|----------|-------|-------|
| Left panel width | 3.0 in | Ink branded panel |
| Left panel inner margin | 0.4 in | Text inset from left edge of panel |
| Left panel text width | 2.2 in | Width of text elements in panel |
| Content area left edge | 3.4 in | Panel width + gap |
| Content area width | 6.2 in | Main content column |
| Content area right edge | 9.6 in | |
| Right margin | 0.4 in | From content edge to slide edge |
| Gap between panel and content | 0.4 in | |

---

## Structural elements (shared across slide types)

### Bottom guide rule

Replaces the old 0.1 in filled accent bar. This identity draws lines, it does not
lay down blocks of colour.

| Property | Value |
|----------|-------|
| y position | 5.525 in |
| Weight | 0.7 pt |
| Width | 10.0 in (full width) |
| Colour | `#BFD3E6` (Guide) |

### Corner triangle (page number background)

| Property | Value |
|----------|-------|
| x | 9.118 in |
| y | -0.018 in |
| w | 0.865 in |
| h | 0.9 in |
| Fill | `#1B3A5C` (Ink) |
| Shape | Right triangle |
| Rotation | 270 degrees |

### Page number badge

| Property | Value |
|----------|-------|
| x | 9.589 in |
| y | 0.109 in |
| Diameter | 0.3 in |
| Fill | `#FFFFFF` |
| Font | Plus Jakarta Sans, 12pt, `#1B3A5C` |
| Alignment | Centre |

### Construction circle (left panel)

Formerly a filled Slate disc. On an ink panel a filled ink circle is invisible,
and filled decoration is no longer part of the identity — so it becomes an
outlined construction circle, echoing the circle in the mark.

| Property | Value |
|----------|-------|
| x | -0.6 in (partially off-slide) |
| y | 3.6 in |
| Diameter | 2.6 in |
| Fill | None |
| Stroke | 0.7 pt `#BFD3E6` (Guide) |
