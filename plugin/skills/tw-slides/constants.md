# TW Slides — Global Constants

Shared values derived from component specs. These are the canonical source — individual component specs reference these.

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

### Accent (Teal/Aqua) — highlights, icons, callouts

| Name | Hex | Role |
|------|-----|------|
| Aqua | `#ADCFC9` | Icon circles, accent borders, subtitle text on dark BG |
| Teal | `#518C94` | Accent dividers, action title text, bottom bars, section markers |
| Warm Tan | `#CEC3A1` | Tertiary neutral |

### Text colours

| Context | Hex |
|---------|-----|
| Body text on light BG | `#3A3A3A` |
| Body text on dark BG | `#FFFFFF` |
| Headings on dark BG | `#FFFFFF` |
| Headings on light BG | `#072E45` or `#0E425B` |
| Muted / source / caption | `#518C94` or `#B8AD90` |

---

## Typography

### Font stack

| Priority | Font | Usage |
|----------|------|-------|
| Primary | Inter Tight | All text elements — set explicitly on every text box |
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

### Line spacing

| Element | Value |
|---------|-------|
| Section subtitle | 130% |
| Action title | 130% |
| Body content | 135% |

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

## Structural elements

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
