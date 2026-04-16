# Component: Left-Third-Title Slide (`left-third-title`)

Used for **Situation** and **Objectives** slides. A branded left panel (section title, subtitle, accent divider, logo) occupies the left third; the right two-thirds carry the content. The layout frame is identical for both slide types — only the section label, the body variant, and the text content change.

**Visual reference:** `left-third-title-examples.pdf` / `left-third-title-examples.pptx` (4 examples: 2 situations + 2 objectives, covering both body variants).

---

## Build workflow

**Default — duplicate from example.** Use the `anthropic-skills:pptx` editing flow (`editing.md`):

1. `python scripts/office/unpack.py left-third-title-examples.pptx unpacked/`
2. Pick the example slide closest to the variant you need (situation vs objectives, columns vs bullets) and duplicate it with `add_slide.py`.
3. Swap text in the duplicated slide's XML — keep `<a:pPr>` and run-property formatting intact.
4. `python scripts/clean.py unpacked/`, then `python scripts/office/pack.py unpacked/ output.pptx --original left-third-title-examples.pptx`.

**Fallback — generate from code.** Use the `pptxgenjs` code template at the bottom of this file when the variant is structurally beyond the four examples (e.g. column counts other than 2/3/4, or a body layout the examples don't cover).

After either path, run the visual-QA loop from `anthropic-skills:pptx`.

---

## Slide properties

| Property | Value |
|----------|-------|
| Width | 10.0 in |
| Height | 5.625 in |
| Background | `#FFFFFF` |
| Aspect ratio | 16:9 |

---

## Fixed frame (always present)

Every slide of this type has the same chrome — left panel, bottom bar, top-right page badge, action title, separator, source citation. Only the body area changes between variants.

### Element inventory — fixed frame

| # | Element | x (in) | y (in) | w (in) | h (in) | Notes |
|---|---------|--------|--------|--------|--------|-------|
| 1 | Left panel background | 0.0 | 0.0 | 3.0 | 5.625 | Fill `#072E45` (Midnight Navy) |
| 2 | Decorative circle | -0.6 | 3.6 | 2.6 | 2.6 | Fill `#134F68` (Slate), partially off-slide |
| 3 | Section title | 0.4 | 1.6 | 2.2 | 0.5 | Inter Tight 28pt bold, `#FFFFFF` |
| 4 | Accent divider | 0.4 | 2.15 | 0.9 | 0.04 | Fill `#518C94` (Teal) |
| 5 | Section subtitle | 0.4 | 2.35 | 2.2 | 0.6 | Inter Tight 10.5pt, `#ADCFC9` (Aqua), line spacing 130% |
| 6 | Logo/icon | 0.85 | 3.5 | 0.6 | 0.6 | PNG |
| 7 | Action title | 3.4 | 0.35 | 6.2 | 0.6 | Inter Tight 12pt bold, `#518C94` (Teal), line spacing 130% |
| 8 | Horizontal separator | 3.4 | 1.05 | 6.2 | 0.0098 | Fill `#E8E8E4` (Light Stone), hairline |
| 9 | Body content area | 3.4 | 1.2025 | 6.2 | 3.9 | Variant-specific — see below |
| 10 | Source citation | 3.4 | 5.15 | 6.2 | 0.25 | Inter Tight 7.5pt italic, `#B8AD90` (Sand) |
| 11 | Bottom accent bar | 0.0 | 5.525 | 10.0 | 0.1 | Fill `#518C94` (Teal), full width |
| 12 | Corner triangle | 9.118 | -0.018 | 0.865 | 0.9 | `rtTriangle`, fill `#072E45`, rotated 270° |
| 13 | Page number badge | 9.589 | 0.109 | 0.3 | 0.3 | White ellipse + Calibri 12pt `#000000` numeral |

---

## Body variants

Pick one of two variants based on content shape.

### Variant `columns`

Body area is divided into N equal-width cards in a row. Default N=3; supports N=2 or N=4.

**Per-card structure (top to bottom):**
- Short coloured top border strip (~0.05 in tall) — rotates through navy `#072E45`, teal `#518C94`, tan `#B8AD90`
- Circular icon badge — navy `#072E45` fill, white glyph, ~0.55 in diameter
- Bold title — Inter Tight 14pt bold, `#072E45`, centred, 1–3 words
- Body text — Inter Tight 11pt regular, `#3A3A3A`, centred, 12–18 words

**Optional "Focus" banner:** A light teal banner (`#ADCFC9` fill, italic dark navy text, ~0.25 in tall) sitting above one of the columns, labelling it as the engagement focus. Used when the client is scoping to one of the columns.

**Word count budgets for `columns`:**
- Column title: **1–3 words** (single noun phrase, e.g. "People Operation")
- Column body: **12–18 words** — 2–3 lines at column width

### Variant `bullets`

Body area holds a vertical bullet list. Two sub-shapes controlled by `numbered`:

**`numbered: false`** — Top-level items prefixed by a solid teal filled circle (`#518C94`, ~0.12 in). Bold lead-in phrase, then continuation text on the same line. Sub-items (optional) prefixed by a smaller grey filled circle (`#6B6B6B`, ~0.08 in), indented ~0.3 in.

**`numbered: true`** — Top-level items prefixed by a large teal filled circle (`#518C94`, ~0.3 in) containing a white numeral. Bold item title, colon, continuation body wrapping under. No sub-items in this sub-shape.

**Typography (both sub-shapes):**
- Top-level title (bold portion): Inter Tight 12pt bold, `#072E45` or `#000000`
- Top-level body (continuation): Inter Tight 12pt regular, `#3A3A3A`, line spacing 135%
- Sub-item: Inter Tight 11pt regular, `#3A3A3A`

**Word count budgets for `bullets`:**
- Item bold lead / title: **3–10 words**
- Item continuation body: **15–30 words** (2–3 lines)
- Sub-item: **8–20 words** (1–2 lines)
- Item count: **3–5 items** (more than 5 becomes cramped)

---

## Word count budgets — fixed frame

| Element | Budget | Notes |
|---------|--------|-------|
| Section label | 1 word | "Situation" or "Objectives" |
| Section subtitle | 6–10 words | Wraps to 2–3 lines in left panel |
| Action title | 15–20 words | 1–2 lines; the slide's conclusion. Above 20 forces a third line on narrow columns and dilutes the punch. |
| Source citation | 10–20 words | Single line |

If content exceeds these budgets, split into two slides rather than shrink type — the template is optimised at these sizes.

---

## Template parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `section_label` | string | Yes | Left panel heading — "Situation" or "Objectives" |
| `section_subtitle` | string | No | 2–3 line description below section label |
| `action_title` | string | Yes | Bold teal conclusion at top of content area |
| `variant` | enum | Yes | `columns` or `bullets` |
| `columns` | array | If `variant=columns` | 2–4 items, each `{ border_color?, icon?, title, body }` |
| `bullets` | object | If `variant=bullets` | `{ numbered: bool, items: [{ title, body, subs?: string[] }] }` |
| `source` | string | No | Source citation at bottom |
| `slide_number` | number | Yes | Integer for page badge |
| `logo_path` | string | No | Path to logo/icon image for left panel |

---

## pptxgenjs code template

```javascript
function addLeftThirdTitle(pptx, {
  slideNumber,
  sectionLabel,
  sectionSubtitle,
  actionTitle,
  variant,         // 'columns' | 'bullets'
  columns,         // [{ borderColor, icon, title, body }]
  bullets,         // { numbered: bool, items: [{ title, body, subs }] }
  source,
  logoPath
}) {
  // --- Constants ---
  const SLIDE_W = 10.0, SLIDE_H = 5.625;
  const PANEL_W = 3.0, PANEL_FILL = '072E45';
  const PANEL_MARGIN = 0.4, PANEL_TEXT_W = 2.2;
  const CIRCLE_X = -0.6, CIRCLE_Y = 3.6, CIRCLE_SIZE = 2.6, CIRCLE_FILL = '134F68';
  const SECTION_TITLE_Y = 1.6, SECTION_TITLE_H = 0.5;
  const FONT = 'Inter Tight';
  const SECTION_TITLE_SIZE = 28;
  const DIVIDER_Y = 2.15, DIVIDER_W = 0.9, DIVIDER_H = 0.04;
  const ACCENT_COLOR = '518C94';
  const SUBTITLE_Y = 2.35, SUBTITLE_H = 0.6, SUBTITLE_SIZE = 10.5;
  const SUBTITLE_COLOR = 'ADCFC9';
  const CONTENT_X = 3.4, CONTENT_W = 6.2;
  const ACTION_TITLE_Y = 0.35, ACTION_TITLE_H = 0.6;
  const ACTION_TITLE_SIZE = 12, ACTION_TITLE_COLOR = '518C94';
  const SEPARATOR_Y = 1.05, SEPARATOR_H = 0.0098, SEPARATOR_COLOR = 'E8E8E4';
  const BODY_Y = 1.2025, BODY_H = 3.9;
  const BODY_SIZE = 12, BODY_COLOR = '3A3A3A';
  const SOURCE_Y = 5.15, SOURCE_H = 0.25, SOURCE_SIZE = 7.5, SOURCE_COLOR = 'B8AD90';
  const BOTTOM_BAR_Y = 5.525, BOTTOM_BAR_H = 0.1;
  const TRIANGLE_X = 9.118, TRIANGLE_Y = -0.018, TRIANGLE_W = 0.865, TRIANGLE_H = 0.9;
  const BADGE_X = 9.589, BADGE_Y = 0.109, BADGE_SIZE = 0.3;

  const slide = pptx.addSlide();
  slide.background = { color: 'FFFFFF' };

  // Left panel
  slide.addShape(pptx.ShapeType.rect, { x: 0, y: 0, w: PANEL_W, h: SLIDE_H, fill: { color: PANEL_FILL } });
  slide.addShape(pptx.ShapeType.ellipse, { x: CIRCLE_X, y: CIRCLE_Y, w: CIRCLE_SIZE, h: CIRCLE_SIZE, fill: { color: CIRCLE_FILL } });
  slide.addText(sectionLabel, {
    x: PANEL_MARGIN, y: SECTION_TITLE_Y, w: PANEL_TEXT_W, h: SECTION_TITLE_H,
    fontFace: FONT, fontSize: SECTION_TITLE_SIZE, bold: true,
    color: 'FFFFFF', align: 'left', margin: 0
  });
  slide.addShape(pptx.ShapeType.rect, { x: PANEL_MARGIN, y: DIVIDER_Y, w: DIVIDER_W, h: DIVIDER_H, fill: { color: ACCENT_COLOR } });
  if (sectionSubtitle) {
    slide.addText(sectionSubtitle, {
      x: PANEL_MARGIN, y: SUBTITLE_Y, w: PANEL_TEXT_W, h: SUBTITLE_H,
      fontFace: FONT, fontSize: SUBTITLE_SIZE, color: SUBTITLE_COLOR,
      align: 'left', lineSpacingMultiple: 1.3, margin: 0
    });
  }
  if (logoPath) slide.addImage({ path: logoPath, x: 0.85, y: 3.5, w: 0.6, h: 0.6 });

  // Action title + separator
  slide.addText(actionTitle, {
    x: CONTENT_X, y: ACTION_TITLE_Y, w: CONTENT_W, h: ACTION_TITLE_H,
    fontFace: FONT, fontSize: ACTION_TITLE_SIZE, bold: true,
    color: ACTION_TITLE_COLOR, align: 'left', lineSpacingMultiple: 1.3, margin: 0
  });
  slide.addShape(pptx.ShapeType.rect, {
    x: CONTENT_X, y: SEPARATOR_Y, w: CONTENT_W, h: SEPARATOR_H,
    fill: { color: SEPARATOR_COLOR }
  });

  // Body (variant-specific)
  if (variant === 'columns') {
    renderColumns(pptx, slide, columns, { x: CONTENT_X, y: BODY_Y, w: CONTENT_W, h: BODY_H });
  } else if (variant === 'bullets') {
    renderBullets(pptx, slide, bullets, { x: CONTENT_X, y: BODY_Y, w: CONTENT_W, h: BODY_H });
  }

  // Source
  if (source) {
    slide.addText(source, {
      x: CONTENT_X, y: SOURCE_Y, w: CONTENT_W, h: SOURCE_H,
      fontFace: FONT, fontSize: SOURCE_SIZE, italic: true,
      color: SOURCE_COLOR, align: 'left', margin: 0
    });
  }

  // Bottom bar + corner badge
  slide.addShape(pptx.ShapeType.rect, { x: 0, y: BOTTOM_BAR_Y, w: SLIDE_W, h: BOTTOM_BAR_H, fill: { color: ACCENT_COLOR } });
  slide.addShape(pptx.ShapeType.rtTriangle, { x: TRIANGLE_X, y: TRIANGLE_Y, w: TRIANGLE_W, h: TRIANGLE_H, fill: { color: PANEL_FILL }, rotate: 270 });
  slide.addShape(pptx.ShapeType.ellipse, { x: BADGE_X, y: BADGE_Y, w: BADGE_SIZE, h: BADGE_SIZE, fill: { color: 'FFFFFF' } });
  slide.addText(String(slideNumber), {
    x: BADGE_X, y: BADGE_Y, w: BADGE_SIZE, h: BADGE_SIZE,
    fontFace: 'Calibri', fontSize: 12, color: '000000',
    align: 'center', valign: 'middle', margin: 0
  });

  return slide;
}
```

`renderColumns` and `renderBullets` are thin helpers that draw inside the supplied `{x, y, w, h}` body slot — the columns helper lays out N cards with top borders, icon, title, body; the bullets helper walks the items array, drawing the circle prefix plus text runs, recursing one level into `subs`.
