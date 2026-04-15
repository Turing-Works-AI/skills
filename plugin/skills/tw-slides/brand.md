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

### Primary (Dark Blues) — backgrounds, headers, section titles

| Name | Hex | Role |
|------|-----|------|
| Midnight Navy | `#072E45` | Title slide backgrounds, dark section backgrounds, left panels |
| Deep Teal | `#0E425B` | Primary brand colour; headers, key shapes |
| Ocean | `#0A3851` | Supporting dark elements |
| Steel Blue | `#1F4C60` | Secondary dark backgrounds |
| Slate | `#134F68` | Alternate header fill, decorative elements |

### Secondary (Warm Neutrals) — slide backgrounds, cards, off-white areas

| Name | Hex | Role |
|------|-----|------|
| Sand | `#B8AD90` | Subtle accent, dividers, source citation text |
| Cream | `#F7EACC` | Light backgrounds, card fills |
| Off-White | `#F9F9F7` | Slide body background (default) |
| Light Stone | `#E8E8E4` | Alternate card/panel fill, separator lines |

### Accent (Teal/Aqua) — highlights, icons, callouts — use sparingly

| Name | Hex | Role |
|------|-----|------|
| Aqua | `#ADCFC9` | Icon circles, accent borders, subtitle text on dark BG |
| Teal | `#518C94` | Accent dividers, action title text, bottom bars, section markers |
| Warm Tan | `#CEC3A1` | Tertiary neutral |

### Component-specific colours

| Hex | Name | Where used |
|-----|------|------------|
| `#F0F7F5` | Light Mint | Table / matrix cell backgrounds |
| `#BBD6EE` | Light Blue | Status badges ("To discuss", "Initial view") |
| `#666666` | Mid Grey | Dashed divider lines |
| `#0D425C` | Dark Teal | Deliverables label text, badge text |

### Text colours

| Context | Hex |
|---------|-----|
| Body text on light BG | `#3A3A3A` |
| Body text on dark BG | `#FFFFFF` |
| Headings on dark BG | `#FFFFFF` |
| Headings on light BG | `#072E45` or `#0E425B` |
| Muted / source / caption | `#518C94` or `#B8AD90` |

### Prohibited colours

- **Orange — never use.** Not part of the Turing Works palette. Has appeared in decks carried over from other clients' source material. Replace any orange with Teal `#518C94` or Aqua `#ADCFC9` (accents) or Deep Teal `#0E425B` (dark elements).
- Any colour not listed in the palette tables above.

### Structural Colour Rule ("Sandwich")

- **Title slide**: Dark (`#072E45`) — white and cream text
- **Content slides**: Light (`#F9F9F7` or white) — dark text, teal accents
- **CTA / section divider slides**: Dark (`#0D425C`) — white text, aqua accents
- **Closing slide**: Dark background, white text

---

## Typography

### Font stack

| Priority | Font | Usage |
|----------|------|-------|
| Primary | Inter Tight (all weights) | All text — set explicitly on every text box |
| Fallback | Calibri | Page numbers, system fallback |
| Never use | Arial, Trebuchet MS | — |

### Font size scale

| Element | Size (pt) | Weight | Colour | Notes |
|---------|-----------|--------|--------|-------|
| Hero/display title (cover) | 52 | Bold | `#FFFFFF` / `#F7EACC` | Cover slide only |
| Section title (left panel) | 28 | Bold | `#FFFFFF` | On dark background |
| Section header / subtitle | 18 | SemiBold | `#0E425B` / `#FFFFFF` | |
| Slide main title (Action Title) | 16 | Bold | `#FFFFFF` (dark BG) / `#072E45` (light BG) | |
| Action title (content-1col variant) | 12 | Bold | `#518C94` | Teal on white BG |
| Body / content text | 11–12 | Regular | `#3A3A3A` | |
| Section subtitle (left panel) | 10.5 | Regular | `#ADCFC9` | On dark background |
| Supporting body / sub-bullets | 10 | Regular | `#3A3A3A` | Minimum font size |
| Labels / captions / source lines | 7.5–10 | Regular/Italic | `#518C94` / `#B8AD90` | |

In pptxgenjs, multiply pt by 100: 16pt → `fontSize: 1600`. Minimum font size on any slide is 10pt — no text may go below this.

### Line spacing

| Element | Value |
|---------|-------|
| Section subtitle | 130% |
| Action title | 130% |
| Body content | 135% |

### Typography rules

- Set Inter Tight explicitly on every text box — never rely on theme defaults
- Titles left-aligned on content slides; centred only on cover/thanks slides
- Source lines ("Source: …") always at bottom of slide, 10pt, muted teal
- Numbered callout badges: bold white text on dark teal circle background
- No italic for body text; reserve for taglines or pull-quotes only

---

## Layout patterns

### Cover / title slide

- Full dark background: `#072E45`
- Client logo + Turing Works wordmark top-left, separated by `×` in cream
- Hero title: 52pt bold white, left-aligned, upper-left quadrant
- Sub-tagline: 14–16pt, cream (`#F7EACC`), below title
- Date + "Confidential" footer: 11pt, `#ADCFC9`, bottom-left

### Standard content slide

- Background: white or `#F9F9F7`
- Slide number badge: dark teal circle, top-right (white number inside)
- Section label: small sentence-case label in teal above main heading (e.g. "Situation", "Proposal")
- Action Title: 16pt bold `#072E45`, top-left — the key message of the slide
- Lead (optional): 11–12pt dark teal, right column or below heading — supplementary context
- Body content: 10–12pt, `#3A3A3A`
- Source line: 10pt `#518C94`, bottom of slide

### Two-column layout

- Left column: text/headings/numbered steps (~55% width)
- Right column: supporting context, icons, or illustrative text (~40% width)
- Use `#ADCFC9` or `#518C94` for icon circles alongside text rows

### Card/grid layout

- 2×2 grid of cards with light fill (`#F9F9F7` or `#E8E8E4`)
- Each card: numbered badge (dark teal), bold short title (14pt), body text (10pt)
- Uniform card padding; consistent border radius (4–6pt)

### Numbered card list (full-width)

- Full-width slide (no left panel); white background
- Action title: **24pt bold Midnight Navy** — larger than standard content slides, leads with impact
- Optional teal lead subtitle (14pt) below the title
- 3–6 stacked horizontal cards in Light Stone (`#E8E8E4`), rounded corners
- Each card: numbered Deep Teal badge (vertically centred), **issue title** (bold navy) and **metric** (teal) on the same line separated by whitespace (not em dash or pipe), description text below spanning full width, category tag pill (bordered, teal italic) vertically centred on right edge
- Use for: issue lists, findings, risk registers, prioritised items
- Full spec: `slide-types/card-list.md`

### Dark CTA / section divider slide

- Background: `#0D425C` or `#072E45`
- Title: 27pt bold white, left-aligned
- Bullets: 14–16pt white, with `#ADCFC9` markers
- No source line needed

### Bio / profile slide

- White background; circular headshot top-left
- Name: 18pt bold `#072E45`; Title: 12pt `#518C94`
- Summary: 10pt `#3A3A3A`; Experience bullets: 10pt `#3A3A3A`

---

## Shape & decoration rules

- **Numbered badges**: Dark teal circles (`#0E425B`) with white bold numbers
- **Icon circles**: `#ADCFC9` or `#518C94` fill, white icon inside
- **No underline accents beneath titles** — use background contrast or whitespace instead
- **Divider lines**: sparingly; `#ADCFC9` at 0.5–1pt
- **No drop shadows or outer glows** — flat and clean only
- **Callout bubbles**: aqua or cream fill, small border, used to annotate charts

---

## Slide structure conventions

- **Slide number**: top-right corner badge on all content slides; hidden on cover and thanks
- **Section label**: short contextual anchor above or beside the Action Title (e.g. "Situation", "Objectives", "Terms")
- **Source line**: bottom of slide, always present if any claim or data is referenced
- **Appendix**: labelled divider slide in dark style, then backup slides follow
- **Closing slide**: "Thanks!" or "Next steps", dark background, white text

---

## Grid constants

| Constant | Value | Notes |
|----------|-------|-------|
| Left panel width | 3.0 in | Dark branded panel |
| Left panel inner margin | 0.4 in | Text inset from left edge of panel |
| Left panel text width | 2.2 in | Width of text elements in panel |
| Content area left edge | 3.4 in | Panel width + gap |
| Content area width | 6.2 in | Main content column |
| Content area right edge | 9.6 in | |
| Right margin | 0.4 in | From content edge to slide edge |
| Gap between panel and content | 0.4 in | |

---

## Structural elements (shared across slide types)

### Bottom accent bar

| Property | Value |
|----------|-------|
| y position | 5.525 in |
| Height | 0.1 in |
| Width | 10.0 in (full width) |
| Fill | `#518C94` (Teal) |

### Corner triangle (page number background)

| Property | Value |
|----------|-------|
| x | 9.118 in |
| y | -0.018 in |
| w | 0.865 in |
| h | 0.9 in |
| Fill | `#072E45` (Midnight Navy) |
| Shape | Right triangle |
| Rotation | 270 degrees |

### Page number badge

| Property | Value |
|----------|-------|
| x | 9.589 in |
| y | 0.109 in |
| Diameter | 0.3 in |
| Fill | `#FFFFFF` |
| Font | Calibri, 12pt, `#000000` |
| Alignment | Centre |

### Decorative circle (left panel)

| Property | Value |
|----------|-------|
| x | -0.6 in (partially off-slide) |
| y | 3.6 in |
| Diameter | 2.6 in |
| Fill | `#134F68` (Slate) |
