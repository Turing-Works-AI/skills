# Component: Three-Column Table with Summary Row (`table-3col`)

A generic table layout derived from the workplan slide. Three equal columns with header pills, multiple content rows, and a summary/deliverables row at the bottom. No left branded panel — full-width content area. Includes title bar, optional status badges, dashed dividers, and footnotes.

This is the generalised table component. The `workplan` component is one specific use of this pattern.

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
│  Title: "Label  |  Action title"           [Page badge]  │
│  [Status badge]                                          │
├──────────────┬──────────┬──────────┬──────────┐          │
│              │ Col 1    │ Col 2    │ Col 3    │          │  ← header pills
│              ├──────────┴──────────┴──────────┤          │
│              │ Optional banner spanning cols   │          │
├──────────────┼──────────┬──────────┬──────────┤          │
│ Row label 1  │ bullets  │ bullets  │ bullets  │          │
├─ ─ ─ ─ ─ ─ ─┼──────────┼──────────┼──────────┤          │
│ Row label 2  │ bullets  │ bullets  │ bullets  │          │
├─ ─ ─ ─ ─ ─ ─┼──────────┼──────────┼──────────┤          │
│ Row label N  │ bullets  │ bullets  │ bullets  │          │
├─ ─ ─ ─ ─ ─ ─┼──────────┼──────────┼──────────┤          │
│ Summary      │ ✓ items  │ ✓ items  │ ✓ items  │          │
├──────────────┴──────────┴──────────┴──────────┤          │
│ Footnotes / Source                             │          │
├────────────────────────────────────────────────┴──────────┤
│ ████████████████ Bottom accent bar ██████████████████████ │
└──────────────────────────────────────────────────────────┘
```

---

## Grid constants

| Constant | Value | Notes |
|----------|-------|-------|
| Grid left edge | 0.5 in | x of row labels |
| Row label width | 1.3 in | |
| Columns left edge | 1.86 in | x of first column |
| Column width | 2.513 in | Each column |
| Column gap | 0.047 in | Between columns |
| Cell content inset x | 0.06 in | Text inset from cell edge |
| Cell content width | 2.393 in | Text area within cell |
| Column 1 x | 1.86 in | |
| Column 2 x | 4.423 in | |
| Column 3 x | 6.987 in | |

---

## Element details

### Title bar

| Property | Value |
|----------|-------|
| Position | x: 0.5 in, y: 0.22 in |
| Size | w: 9.0 in, h: 0.55 in |
| Fill | None |
| Anchor | Top |

**Text (multi-run):**

| Run | Content | Font | Size | Weight | Colour |
|-----|---------|------|------|--------|--------|
| 1 | `{{section_label}}` | Inter Tight | 16pt | Bold | `#518C94` |
| 2 | `"  \|  "` | Inter Tight | 16pt | Regular | `#E8E8E4` |
| 3 | `{{action_title}}` | Inter Tight | 16pt | Regular | `#072E45` |

### Column header pills

| Property | Value |
|----------|-------|
| Shape | Rounded rectangle, corner radius adj = 12500 |
| Size | w: 2.513 in, h: 0.240 in |
| Fill | `#072E45` (Midnight Navy) |
| Text | `{{column_header}}`, Inter Tight, 8pt, Bold, `#FFFFFF`, Centre |

### Row labels

Rounded rectangle pill + text overlay, centre aligned.

| Property | Value |
|----------|-------|
| Width | 1.3 in |
| Height | Varies by row (0.52–0.72 in) |
| Corner radius | adj = 12500 |
| Fill | Varies by row (see colour mapping below) |

**Row label colour rotation:**

| Position | Fill | Usage |
|----------|------|-------|
| Row 1 | `#072E45` (Midnight Navy) | Primary category |
| Row 2 | `#518C94` (Teal) | Secondary category |
| Row 3 | `#B8AD90` (Sand) | Tertiary category |
| Row 4+ | Cycle through above | |
| Summary row | None (transparent) | Label text in `#0D425C` |

**Label text:**

| Line | Font | Size | Weight | Colour |
|------|------|------|--------|--------|
| Primary | Inter Tight | 8pt | Bold | `#FFFFFF` |
| Sub-label | Inter Tight | 7pt | Regular | `#FFFFFF` |

### Content cells

**Background:**

| Property | Value |
|----------|-------|
| Fill | `#F0F7F5` (Light Mint) |
| Border | 0.75pt solid `#ADCFC9` |

**Text:**

| Property | Value |
|----------|-------|
| Font | Inter Tight |
| Size | 5.5pt |
| Weight | Regular |
| Colour | `#072E45` |
| Alignment | Left |
| Anchor | Top |
| Line spacing | 108% |
| Bullet | `●` disc, `#072E45` |

### Summary row cells

Same cell background as content cells.

| Property | Value |
|----------|-------|
| Font | Inter Tight |
| Size | 6.5pt |
| Weight | Bold |
| Colour | `#072E45` |
| Line spacing | 108% |
| Prefix | `✓` (checkmark in text) |

### Dashed divider lines

Horizontal dashed lines separating row groups.

| Property | Value |
|----------|-------|
| x | 0.539 in |
| Width | 8.96 in |
| Stroke | 0.75pt, dashed, `#666666` |

### Optional spanning banner

Rounded rect spanning all three columns, placed between headers and first row.

| Property | Value |
|----------|-------|
| Height | 0.22 in |
| Fill | `#F0F7F5` |
| Border | 0.75pt `#ADCFC9`, corner radius adj = 13636 |
| Text | Inter Tight, 7pt, `#072E45`, Centre |

### Footnotes / source

| Property | Value |
|----------|-------|
| Position | x: 0.842 in, y: 5.086 in |
| Size | w: 9.0 in, h: 0.2 in |
| Anchor | Bottom |
| Line 1 | `{{footnotes}}`, Inter Tight, 8pt, Regular, `#B8AD90` |
| Line 2 | `{{source}}`, Inter Tight, 8pt, Italic, `#B8AD90` |

### Corner triangle + page badge

| Element | x | y | w | h | Fill |
|---------|---|---|---|---|------|
| Triangle | 9.118 in | -0.018 in | 0.865 in | 0.9 in | `#072E45`, rotation -90° |
| Badge | 9.589 in | 0.109 in | 0.3 in | 0.3 in | `#FFFFFF` |
| Badge text | `{{slide_number}}`, Calibri, 12pt, `#000000`, Centre |

### Bottom accent bar

| Property | Value |
|----------|-------|
| y | 5.525 in |
| Size | w: 10.0 in, h: 0.1 in |
| Fill | `#518C94` |

---

## Template parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `section_label` | string | Yes | Left part of title (bold teal) |
| `action_title` | string | Yes | Right part of title (conclusion statement) |
| `sticker` | string | No | Status badge (e.g. "To discuss") |
| `columns` | object[] | Yes | Array of 3 column header objects with `label` |
| `rows` | object[] | Yes | Array of row objects (see below) |
| `summary_label` | string | Yes | Label for summary row (e.g. "Deliverables", "Key outcomes") |
| `summary` | object[] | Yes | Array of 3 arrays of summary items per column |
| `banner` | string | No | Optional spanning banner text |
| `footnotes` | string | No | Footnote text |
| `source` | string | No | Source citation |
| `slide_number` | number | Yes | Page number |

### Row object

```yaml
rows:
  - label: "Row category name"
    sub_label: "Optional sub-label"     # optional
    colour: "#072E45"                   # optional, defaults to rotation
    cells:
      - # Column 1 bullets
        - "Bullet point one"
        - "Bullet point two"
      - # Column 2 bullets
        - "Bullet point one"
      - # Column 3 bullets
        - "Bullet point one"
```

### Summary object

```yaml
summary:
  - # Column 1
    - "Summary item one"
    - "Summary item two"
  - # Column 2
    - "Summary item one"
  - # Column 3
    - "Summary item one"
```

---

## pptxgenjs code template

```javascript
function addTable3ColSlide(pptx, {
  slideNumber,
  sectionLabel,
  actionTitle,
  sticker,
  columns,
  rows,
  summaryLabel,
  summary,
  banner,
  footnotes,
  source
}) {
  // --- Grid constants ---
  const SLIDE_W = 10.0;
  const GRID_LEFT = 0.5;
  const ROW_LABEL_W = 1.3;
  const COL_LEFT = 1.86;
  const COL_W = 2.513;
  const COL_GAP = 0.047;
  const CELL_INSET_X = 0.06;
  const CELL_CONTENT_W = 2.393;
  const PILL_H = 0.240;
  const PILL_RADIUS = 0.08;

  // --- Colours ---
  const NAVY = '072E45';
  const TEAL = '518C94';
  const SAND = 'B8AD90';
  const MINT = 'F0F7F5';
  const CELL_BORDER = 'ADCFC9';
  const LIGHT_BLUE = 'BBD6EE';
  const DIVIDER_GREY = '666666';
  const SEPARATOR = 'E8E8E4';
  const DARK_TEAL = '0D425C';
  const ROW_COLOURS = [NAVY, TEAL, SAND];

  // --- Typography ---
  const FONT = 'Inter Tight';

  const slide = pptx.addSlide();
  slide.background = { color: 'FFFFFF' };

  const colX = columns.map((_, i) => COL_LEFT + i * (COL_W + COL_GAP));

  // Title bar
  slide.addText([
    { text: sectionLabel, options: { fontFace: FONT, fontSize: 16, bold: true, color: TEAL } },
    { text: '  |  ', options: { fontFace: FONT, fontSize: 16, color: SEPARATOR } },
    { text: actionTitle, options: { fontFace: FONT, fontSize: 16, color: NAVY } }
  ], { x: GRID_LEFT, y: 0.22, w: 9.0, h: 0.55, valign: 'top', margin: 0 });

  // Status badge
  if (sticker) {
    slide.addShape(pptx.ShapeType.rect, {
      x: 3.399, y: -0.012, w: 2.703, h: 0.2,
      fill: { color: LIGHT_BLUE }, line: { color: '333333', width: 0.75 }
    });
    slide.addText(sticker, {
      x: 3.399, y: -0.012, w: 2.703, h: 0.2,
      fontFace: FONT + ' Light', fontSize: 12, color: NAVY,
      align: 'center', margin: 0
    });
  }

  // Column header pills
  columns.forEach((col, i) => {
    slide.addShape(pptx.ShapeType.roundRect, {
      x: colX[i], y: 1.011, w: COL_W, h: PILL_H,
      fill: { color: NAVY }, rectRadius: PILL_RADIUS
    });
    slide.addText(col.label, {
      x: colX[i], y: 1.011, w: COL_W, h: PILL_H,
      fontFace: FONT, fontSize: 8, bold: true, color: 'FFFFFF',
      align: 'center', valign: 'middle', margin: 0
    });
  });

  // Optional banner
  let contentStartY = 1.35;
  if (banner) {
    const bannerW = colX[2] + COL_W - COL_LEFT;
    slide.addShape(pptx.ShapeType.roundRect, {
      x: COL_LEFT, y: 1.286, w: bannerW, h: 0.22,
      fill: { color: MINT }, line: { color: CELL_BORDER, width: 0.75 },
      rectRadius: 0.08
    });
    slide.addText(banner, {
      x: COL_LEFT, y: 1.286, w: bannerW, h: 0.22,
      fontFace: FONT, fontSize: 7, color: NAVY,
      align: 'center', valign: 'middle', margin: 0
    });
    contentStartY = 1.551;
  }

  // Content rows
  const rowSpacing = 0.73;
  rows.forEach((row, rowIdx) => {
    const rowY = contentStartY + rowIdx * rowSpacing;
    const rowH = 0.62 + (row.cells.some(c => c.length > 3) ? 0.1 : 0);
    const labelColour = row.colour || ROW_COLOURS[rowIdx % ROW_COLOURS.length];

    // Row label
    slide.addShape(pptx.ShapeType.roundRect, {
      x: GRID_LEFT, y: rowY, w: ROW_LABEL_W, h: rowH,
      fill: { color: labelColour }, rectRadius: PILL_RADIUS
    });
    const labelRuns = row.sub_label
      ? [
          { text: row.label, options: { fontFace: FONT, fontSize: 8, bold: true, color: 'FFFFFF', breakType: 'none' } },
          { text: row.sub_label, options: { fontFace: FONT, fontSize: 7, color: 'FFFFFF' } }
        ]
      : row.label;
    slide.addText(labelRuns, {
      x: GRID_LEFT, y: rowY, w: ROW_LABEL_W, h: rowH,
      fontFace: FONT, fontSize: 8, bold: true, color: 'FFFFFF',
      align: 'center', valign: 'middle', margin: 0
    });

    // Cells
    row.cells.forEach((bullets, colIdx) => {
      slide.addShape(pptx.ShapeType.rect, {
        x: colX[colIdx], y: rowY, w: COL_W, h: rowH,
        fill: { color: MINT }, line: { color: CELL_BORDER, width: 0.75 }
      });
      slide.addText(
        bullets.map(b => ({
          text: `● ${b}`,
          options: { fontFace: FONT, fontSize: 5.5, color: NAVY, breakType: 'none' }
        })),
        {
          x: colX[colIdx] + CELL_INSET_X, y: rowY + 0.03,
          w: CELL_CONTENT_W, h: rowH - 0.06,
          valign: 'top', lineSpacingMultiple: 1.08, margin: 0
        }
      );
    });

    // Dashed divider after each row (except last before summary)
    if (rowIdx < rows.length - 1) {
      slide.addShape(pptx.ShapeType.line, {
        x: 0.539, y: rowY + rowH + 0.03, w: 8.96, h: 0,
        line: { color: DIVIDER_GREY, width: 0.75, dashType: 'dash' }
      });
    }
  });

  // Dashed divider before summary
  const summaryDivY = contentStartY + rows.length * rowSpacing - 0.05;
  slide.addShape(pptx.ShapeType.line, {
    x: 0.539, y: summaryDivY, w: 8.96, h: 0,
    line: { color: DIVIDER_GREY, width: 0.75, dashType: 'dash' }
  });

  // Summary row
  const summaryY = summaryDivY + 0.05;
  const summaryH = 0.52;

  slide.addText(summaryLabel, {
    x: GRID_LEFT, y: summaryY, w: ROW_LABEL_W, h: summaryH,
    fontFace: FONT, fontSize: 8, bold: true, color: DARK_TEAL,
    align: 'center', valign: 'middle', margin: 0
  });

  summary.forEach((items, colIdx) => {
    slide.addShape(pptx.ShapeType.rect, {
      x: colX[colIdx], y: summaryY, w: COL_W, h: summaryH,
      fill: { color: MINT }, line: { color: CELL_BORDER, width: 0.75 }
    });
    slide.addText(
      items.map(item => ({
        text: `✓ ${item}`,
        options: { fontFace: FONT, fontSize: 6.5, bold: true, color: NAVY, breakType: 'none' }
      })),
      {
        x: colX[colIdx] + CELL_INSET_X, y: summaryY + 0.03,
        w: CELL_CONTENT_W, h: summaryH - 0.06,
        valign: 'top', lineSpacingMultiple: 1.08, margin: 0
      }
    );
  });

  // Footnotes / source
  const footText = [];
  if (footnotes) footText.push({ text: footnotes, options: { fontFace: FONT, fontSize: 8, color: SAND } });
  if (source) footText.push({ text: source, options: { fontFace: FONT, fontSize: 8, italic: true, color: SAND } });
  if (footText.length) {
    slide.addText(footText, { x: 0.842, y: 5.086, w: 9.0, h: 0.2, valign: 'bottom', margin: 0 });
  }

  // Bottom bar
  slide.addShape(pptx.ShapeType.rect, {
    x: 0, y: 5.525, w: SLIDE_W, h: 0.1, fill: { color: TEAL }
  });

  // Corner triangle + page badge
  slide.addShape(pptx.ShapeType.rtTriangle, {
    x: 9.118, y: -0.018, w: 0.865, h: 0.9, fill: { color: NAVY }, rotate: 270
  });
  slide.addShape(pptx.ShapeType.ellipse, {
    x: 9.589, y: 0.109, w: 0.3, h: 0.3, fill: { color: 'FFFFFF' }
  });
  slide.addText(String(slideNumber), {
    x: 9.589, y: 0.109, w: 0.3, h: 0.3,
    fontFace: 'Calibri', fontSize: 12, color: '000000',
    align: 'center', valign: 'middle', margin: 0
  });

  return slide;
}
```
