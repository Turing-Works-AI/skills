---
name: turing-works-brand
description: >-
  The Turing Works (TW) visual identity, covering the symbol, colour palette, typography and layout rules, and how to apply them. Use this skill whenever James asks for anything that carries the Turing Works brand (slides, decks, one-pagers, proposals, documents, website pages, charts, social images, email signatures, case studies, Notion pages, or any artefact a client or prospect will see). Also use it whenever he mentions the TW logo, mark, symbol, brand colours, blueprint blue, vermilion, Plus Jakarta Sans, "the chain", or asks whether something is on brand. Trigger even if he only says "make it look like TW" or "brand this". Do not use for Mr Pip product UI unless he says the two should match.
---

# Turing Works brand

Everything visual follows one idea: **accuracy**. The tagline that carries it is
*things that weren't made to align, aligned.* The positioning it serves is
"we build the data function for VC-backed B2B SaaS; every number reconciles to
source, or you don't pay."

Every decision below exists to make that idea visible. If a choice doesn't
serve it, don't make it.

## 1. Symbol: the chain

A triangle, a square and a circle, overlapping on a shared baseline. The
overlap is **deliberately imperfect**: the shapes were not designed to fit,
and they've been made to. That's the story. Do not "fix" it into a tidy
inscribed or tangent construction.

Each shape is individually exact (true equilateral, true square, true circle).
Only the placement is off-grid. Sloppy shapes read as careless; exact shapes
placed imperfectly read as considered.

### Geometry (canonical coordinates, 140 × 76 unit box)

```
triangle  M0 75  L40 5.7  L80 75  Z        (equilateral, side 80, apex at x=40)
square    x=20  y=0  w=70  h=70
circle    cx=100  cy=35  r=38
```

The triangle's base sits 5 units below the square's base. Keep that.

### Rendering rules

- Stroke only, no fills, in **ink** (see colours). Stroke weight ≈ 5 units at
  the canonical size; scale with the mark. Round line joins.
- **Vermilion fills the overlaps only**: the region where the triangle
  intersects the square, and where the circle intersects the square. Nothing
  else on the mark is coloured.
- Minimum size 32 px wide. Below ~48 px drop the vermilion and use the mono
  version.
- Never rotate, mirror, add a container, add a gradient, or change the order
  (triangle → square → circle reads as "resolving"; keep it).

Ready-made files:
- `assets/mark.svg` — ink stroke, vermilion overlaps (primary)
- `assets/mark-mono.svg` — ink only (favicon, small sizes, single-colour)

### Lockup

Mark at 64 × 35 px, 14 px gap, wordmark "Turing Works" in Plus Jakarta Sans
600 at 17 px, letter-spacing -0.01em, ink colour. Optional descriptor to the
right in 12 px blue-grey: "Data, analytics and AI for B2B SaaS".

## 2. Colour

Ink on paper, like a technical drawing that has been checked with a red pen.

| Role   | Name           | Hex       | Job |
|--------|----------------|-----------|-----|
| Ink    | Blueprint blue | `#1B3A5C` | All finished things: type, lines, the mark, chart lines |
| Paper  | Warm off-white | `#F4F1EA` | The surface. Never pure white in print or marketing |
| Pen    | Vermilion      | `#D9432A` | **Only where two things meet**: the mark's overlaps, the reconciled number, the one thing on a page to look at |
| Guide  | Pale blueprint | `#BFD3E6` | Grids, baselines, axes, construction lines. Shows the work; never carries meaning |
| Muted  | Blue-grey      | `#5C7189` | Secondary text, captions, table headers, axis labels |

### Rules

1. **Vermilion appears at most once per page** apart from the mark. Never a
   background, button fill, heading, or state colour. If it's on two things,
   one of them is wrong.
2. **Guide lines are always visible somewhere.** A page with no guides has
   forgotten what the brand is. Use them as faint baselines, margins, and
   chart gridlines.
3. **No black.** The ink is blue. If something needs to be darker, make it
   smaller or move it.
4. **No green, no purple, no gradients, no neutral grey surfaces.**
5. **White is the screen surface** (LinkedIn, email, Notion, embedded UI);
   paper is the print and marketing surface. Same ink, same pen on both.

## 3. Type

**One family: Plus Jakarta Sans.** Google Fonts, so it's in Google Slides
natively and free to install and embed in PowerPoint on Mac and Windows.

- **Two weights only**: 400 (body) and 600 (headlines, wordmark, emphasis).
- **Tabular figures on everywhere a number can sit in a column**
  (`font-variant-numeric: tabular-nums` on the web; in Slides and PowerPoint
  the default figures are used, so right-align every number column and check
  that `1111` is as wide as `8888`).
- Headlines: 28–34 px, weight 600, line-height 1.15–1.2, letter-spacing
  -0.015em. Sentence case. Full stops on headline sentences.
- Body: 14–15 px, weight 400, line-height 1.6, ink or blue-grey.
- Captions and labels: 11–12 px, blue-grey.
- Never mix in a second family, a mono, or a serif. Numbers in tables are the
  same font with tabular figures, not a mono.

## 4. Layout

- Generous paper margins. One or two faint guide lines crossing the page
  (a baseline under the header, a vertical at the left margin) in the guide
  colour, 0.7 px.
- Cards: 0.8 px ink border, 8 px radius, paper fill. No shadows.
- Hierarchy comes from size, spacing and colour before weight.
- One idea per slide or page. One vermilion element.

## 5. Charts

The signature chart is **the reconciliation chart**: two or more lines from
different sources (solid for the primary, dashed for the others), pale guide
gridlines, and a single vermilion point where the sources agree, labelled
"reconciled". Use it on every case study. Axis labels in blue-grey, 10–11 px.
No legend boxes; label the lines directly.

For tables: ink text, blue-grey header row, 0.7 px guide-colour rules,
right-aligned tabular figures, the reconciled row or delta in vermilion 600.

## 6. Copy tone

Plain, direct, British English. Short sentences. Lead with the promise
("Every number reconciles to source. Or you don't pay."), then what we build,
then the free door-opener ("Accuracy audit, two hours, free"). No "insights",
no "unlock", no "journey", no exclamation marks.

## 7. Checklist before anything ships

- [ ] Mark is the original chain, imperfect overlap intact, stroke in ink
- [ ] Vermilion on the mark's overlaps and at most one other place
- [ ] Guide lines visible somewhere on the page
- [ ] No black, no green, no purple, no gradients
- [ ] Plus Jakarta Sans only, weights 400 and 600 only
- [ ] Every number column right-aligned with tabular figures
- [ ] Paper surface for print and marketing, white only for screen contexts
- [ ] One idea, one vermilion, one font

See `references/sample-page.html` for a complete reference page that applies
every rule above. Open it in a browser to check any new artefact against it.
