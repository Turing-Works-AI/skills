# Component: Workplan Slide (`workplan`)

A matrix/grid layout showing a week-by-week workplan across multiple workstreams. Features week column headers (pills), workstream row labels, content cells with bullet lists, a deliverables row, and structural elements (divider lines, banners, footnotes). Highly structured — the grid dimensions scale based on the number of weeks and workstreams.

---

> **Content guide:** See `content/workplan.md` for what to write on this slide.

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
│  Title bar: "Workplan  |  Action title"                  │  ← 0.22" top
│  [To discuss badge]                    [Page badge]      │
├──────────────┬──────────┬──────────┬──────────┬──────────┤
│              │ Week 1   │ Week 2   │ Week 3   │          │  ← column pills
│              ├──────────┴──────────┴──────────┤          │
│              │ Ongoing engagement banner       │          │
├──────────────┼──────────┬──────────┬──────────┤          │
│ Workstream 1 │ bullets  │ bullets  │ bullets  │          │  ← row 1
├──────────────┼──────────┼──────────┼──────────┤          │
│ Workstream 2 │ bullets  │ bullets  │ bullets  │          │  ← row 2
├──────────────┼──────────┼──────────┼──────────┤          │
│ Workstream 3 │ bullets  │ bullets  │ bullets  │          │  ← row 3
├ ─ ─ ─ ─ ─ ─ ┼──────────┼──────────┼──────────┤          │
│ Deliverables │ ✓ items  │ ✓ items  │ ✓ items  │          │  ← deliverables
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
| Grid left edge (row labels) | 0.5 in | x of row label elements |
| Row label width | 1.3 in | Width of workstream label pills |
| Content columns left edge | 1.86 in | x of first week column |
| Column width | 2.513 in | Width of each week column |
| Column gap | 0.047 in | Derived: col2_x − (col1_x + col1_w) |
| Cell content inset from cell bg | 0.06 in | x offset of text from cell background |
| Cell content width | 2.393 in | Text area within each cell |
| Column 1 x | 1.86 in | Week 1 |
| Column 2 x | 4.423 in | Week 2 |
| Column 3 x | 6.987 in | Week 3 |

### Row positions (y values)

| Row | y (in) | Height (in) |
|-----|--------|-------------|
| Week header pills | 1.011 | 0.240 |
| Ongoing banner | 1.286 | 0.220 |
| Workstream 1 | 1.551 | 0.620 |
| Workstream 2 | 2.274 | 0.720 |
| Workstream 3 | 3.034 | 0.720 |
| Deliverables | 3.854 | 0.520 |
| Dashed divider 1 y | 2.218 | — |
| Dashed divider 2 y | 3.802 | — |

---

## Element details

### Title bar

| Property | Value |
|----------|-------|
| Position | x: 0.5 in, y: 0.22 in |
| Size | w: 9.0 in, h: 0.55 in |
| Fill | None |
| Text insets | 0 all sides |
| Anchor | Top |

**Text structure (multi-run):**

| Run | Content | Font | Size | Weight | Colour |
|-----|---------|------|------|--------|--------|
| 1 | `{{section_label}}` (e.g. "Workplan") | Inter Tight | 16pt | Bold | `#518C94` |
| 2 | `"  \|  "` (pipe separator) | Inter Tight | 16pt | Regular | `#E8E8E4` |
| 3 | `{{action_title}}` | Inter Tight | 16pt | Regular | `#072E45` |

### "To discuss" / status badge

| Property | Value |
|----------|-------|
| Position | x: 3.399 in, y: -0.012 in |
| Size | w: 2.703 in, h: 0.2 in |
| Fill | `#BBD6EE` (light blue) |
| Border | 0.75pt, scheme DARK_2 |
| Text | `{{sticker}}` (e.g. "To discuss") |
| Font | Inter Tight Light, 12pt, `#072E45`, Centre |

### "Initial view" banner

| Property | Value |
|----------|-------|
| Position | x: 4.738 in, y: 0.759 in |
| Size | w: 4.747 in, h: 0.192 in |
| Fill | `#BBD6EE` (light blue) |
| Text | `{{status_label}}` (e.g. "Initial view"), Inter Tight → Trebuchet MS 9pt italic `#0D425C`, Right aligned |

### Week column header pills

Each week header is two overlapping shapes: a rounded rect background + transparent text overlay.

| Property | Value |
|----------|-------|
| Shape | Rounded rectangle |
| Corner radius | adj = 12500 |
| Size | w: 2.513 in, h: 0.240 in |
| Fill | `#072E45` (Midnight Navy) |
| Text | `{{week_label}}` (e.g. "Week 1") |
| Font | Inter Tight, 8pt, Bold, `#FFFFFF`, Centre |

### Ongoing engagement banner (grouped)

| Property | Value |
|----------|-------|
| Position | x: 1.86 in, y: 1.286 in |
| Size | w: 7.64 in, h: 0.220 in |
| Background | Rounded rect, `#F0F7F5`, border 0.75pt `#ADCFC9`, corner radius adj = 13636 |
| Text | `{{ongoing_message}}`, Inter Tight, 7pt, `#072E45`, Centre |

### Workstream row labels

Each row label is a rounded rect background + text overlay.

| Property | Value |
|----------|-------|
| Size | w: 1.3 in, h: varies by row |
| Corner radius | adj = 12500 |
| Text | Centre aligned, multi-paragraph |

**Row label colour mapping:**

| Row type | Fill colour | Example |
|----------|------------|---------|
| Primary workstream | `#072E45` (Midnight Navy) | Client team name |
| Secondary workstream | `#518C94` (Teal) | Workshops & Upskilling |
| Tertiary workstream | `#B8AD90` (Sand/Gold) | AI Automations |
| Deliverables | None (transparent) | "Deliverables" text in `#0D425C` |

**Row label text:**

| Run | Font | Size | Weight | Colour |
|-----|------|------|--------|--------|
| Line 1 (main label) | Inter Tight | 8pt | Bold | `#FFFFFF` |
| Line 2 (sub-label) | Inter Tight | 7pt | Regular | `#FFFFFF` |

### Content cells

Each cell is a rect background + text overlay.

**Cell background:**

| Property | Value |
|----------|-------|
| Fill | `#F0F7F5` (light mint) |
| Border | 0.75pt solid `#ADCFC9` |

**Cell text:**

| Property | Value |
|----------|-------|
| Font | Inter Tight |
| Size | 5.5pt |
| Weight | Regular |
| Colour | `#072E45` |
| Alignment | Left |
| Anchor | Top |
| Line spacing | 108% |
| Bullet | `●` disc, Inter Tight, 5.5pt, `#072E45` |
| Text insets | 0 all sides |

### Deliverables cells

Same cell background as content cells. Text differs:

| Property | Value |
|----------|-------|
| Font | Inter Tight |
| Size | 6.5pt |
| Weight | Bold |
| Colour | `#072E45` |
| Line spacing | 108% |
| Bullet | `✓` prefix (text, not bullet character) |

### Dashed divider lines

| Property | Value |
|----------|-------|
| Type | Line / straight connector |
| x | 0.539 in |
| Width | 8.96 in |
| Stroke | 0.75pt, dashed, `#666666` |
| Heads | None |

### Footnotes / source

| Property | Value |
|----------|-------|
| Position | x: 0.842 in, y: 5.086 in |
| Size | w: 9.0 in, h: 0.2 in |
| Anchor | Bottom |
| **Paragraph 1** | `{{footnotes}}`, Inter Tight, 8pt, Regular, `#B8AD90` |
| **Paragraph 2** | `{{source}}`, Inter Tight, 8pt, Italic, `#B8AD90` |

### Corner triangle + page number badge

Same as situation slide spec:

| Element | x | y | w | h | Fill |
|---------|---|---|---|---|------|
| Triangle | 9.118 in | -0.018 in | 0.865 in | 0.9 in | `#072E45`, rotation -90° |
| Badge | 9.589 in | 0.109 in | 0.3 in | 0.3 in | `#FFFFFF` |
| Badge text | `{{slide_number}}`, Calibri, 12pt, `#000000`, Centre |

### Bottom accent bar

| Property | Value |
|----------|-------|
| Position | x: 0.0 in, y: 5.525 in |
| Size | w: 10.0 in, h: 0.1 in |
| Fill | `#518C94` (Teal) |

---

## New colours (not in situation/objectives)

| Hex | Name | Usage |
|-----|------|-------|
| `#F0F7F5` | Light Mint | Cell backgrounds |
| `#BBD6EE` | Light Blue | Status badges ("To discuss", "Initial view") |
| `#666666` | Mid Grey | Dashed divider lines |
| `#0D425C` | Dark Teal | Deliverables label text, badge text |

---

## Template parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `section_label` | string | Yes | Left part of title bar (e.g. "Workplan") |
| `action_title` | string | Yes | Right part of title bar (conclusion statement) |
| `sticker` | string | No | Status badge text (e.g. "To discuss", "Preliminary") |
| `status_label` | string | No | Banner label (e.g. "Initial view") |
| `weeks` | object[] | Yes | Array of week objects with `label` (e.g. "Week 1") |
| `workstreams` | object[] | Yes | Array of workstream objects (see below) |
| `ongoing_message` | string | No | Text for the ongoing engagement banner |
| `deliverables` | object[] | Yes | Array of deliverables per week |
| `footnotes` | string | No | Footnote text |
| `source` | string | No | Source citation |
| `slide_number` | number | Yes | Page number |

### Workstream object

```yaml
workstreams:
  - label: "Workstream name"
    sub_label: "Optional sub-label"
    colour: "#072E45"  # Row label fill
    cells:
      - # Week 1 bullets
        - "Bullet point one"
        - "Bullet point two"
      - # Week 2 bullets
        - "Bullet point one"
      - # Week 3 bullets
        - "Bullet point one"
```

### Deliverables object

```yaml
deliverables:
  - # Week 1
    - "Current-state tool map"
    - "Automation opportunity register (draft)"
  - # Week 2
    - "Prioritised automation opportunities"
  - # Week 3
    - "Automation roadmap with ROI benchmarks"
```

---

## pptxgenjs code template

```javascript
function addWorkplanSlide(pptx, {
  slideNumber,
  sectionLabel,
  actionTitle,
  sticker,
  statusLabel,
  weeks,
  workstreams,
  ongoingMessage,
  deliverables,
  footnotes,
  source
}) {
  // --- Grid constants ---
  const SLIDE_W = 10.0;
  const SLIDE_H = 5.625;
  const GRID_LEFT = 0.5;
  const ROW_LABEL_W = 1.3;
  const COL_LEFT = 1.86;
  const COL_W = 2.513;
  const COL_GAP = 0.047;
  const CELL_INSET_X = 0.06;
  const CELL_CONTENT_W = 2.393;
  const PILL_H = 0.240;
  const PILL_RADIUS = 0.08; // approx from adj=12500

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

  // --- Typography ---
  const FONT = 'Inter Tight';
  const TITLE_SIZE = 16;
  const HEADER_SIZE = 8;
  const CELL_SIZE = 5.5;
  const DELIV_SIZE = 6.5;
  const FOOTNOTE_SIZE = 8;
  const CELL_LINE_SPACING = 1.08;

  // --- Build slide ---
  const slide = pptx.addSlide();
  slide.background = { color: 'FFFFFF' };

  // Column x positions
  const colX = weeks.map((_, i) => COL_LEFT + i * (COL_W + COL_GAP));

  // Title bar
  slide.addText([
    { text: sectionLabel, options: { fontFace: FONT, fontSize: TITLE_SIZE, bold: true, color: TEAL } },
    { text: '  |  ', options: { fontFace: FONT, fontSize: TITLE_SIZE, color: SEPARATOR } },
    { text: actionTitle, options: { fontFace: FONT, fontSize: TITLE_SIZE, color: NAVY } }
  ], {
    x: GRID_LEFT, y: 0.22, w: 9.0, h: 0.55,
    valign: 'top', margin: 0
  });

  // Status badge (optional)
  if (sticker) {
    slide.addShape(pptx.ShapeType.rect, {
      x: 3.399, y: -0.012, w: 2.703, h: 0.2,
      fill: { color: LIGHT_BLUE },
      line: { color: '333333', width: 0.75 }
    });
    slide.addText(sticker, {
      x: 3.399, y: -0.012, w: 2.703, h: 0.2,
      fontFace: FONT + ' Light', fontSize: 12, color: NAVY,
      align: 'center', margin: 0
    });
  }

  // Week column pills
  weeks.forEach((week, i) => {
    const x = colX[i];
    const y = 1.011;
    slide.addShape(pptx.ShapeType.roundRect, {
      x, y, w: COL_W, h: PILL_H,
      fill: { color: NAVY }, rectRadius: PILL_RADIUS
    });
    slide.addText(week.label, {
      x, y, w: COL_W, h: PILL_H,
      fontFace: FONT, fontSize: HEADER_SIZE, bold: true,
      color: 'FFFFFF', align: 'center', valign: 'middle', margin: 0
    });
  });

  // Ongoing engagement banner (optional)
  if (ongoingMessage) {
    const bannerX = COL_LEFT;
    const bannerW = colX[colX.length - 1] + COL_W - COL_LEFT;
    slide.addShape(pptx.ShapeType.roundRect, {
      x: bannerX, y: 1.286, w: bannerW, h: 0.22,
      fill: { color: MINT },
      line: { color: CELL_BORDER, width: 0.75 },
      rectRadius: 0.08
    });
    slide.addText(ongoingMessage, {
      x: bannerX, y: 1.286, w: bannerW, h: 0.22,
      fontFace: FONT, fontSize: 7, color: NAVY,
      align: 'center', valign: 'middle', margin: 0
    });
  }

  // Row heights and y positions (computed dynamically)
  const ROW_START_Y = 1.551;
  const rowColours = [NAVY, TEAL, SAND]; // Default row label colours

  // Workstream rows
  workstreams.forEach((ws, rowIdx) => {
    const rowY = ROW_START_Y + rowIdx * 0.73; // approximate row spacing
    const rowH = ws.cells[0].length > 3 ? 0.72 : 0.62; // taller for more content
    const labelColour = ws.colour || rowColours[rowIdx % rowColours.length];

    // Row label pill
    slide.addShape(pptx.ShapeType.roundRect, {
      x: GRID_LEFT, y: rowY, w: ROW_LABEL_W, h: rowH,
      fill: { color: labelColour }, rectRadius: PILL_RADIUS
    });
    const labelText = ws.sub_label
      ? [
          { text: ws.label, options: { fontFace: FONT, fontSize: HEADER_SIZE, bold: true, color: 'FFFFFF', breakType: 'none' } },
          { text: ws.sub_label, options: { fontFace: FONT, fontSize: 7, color: 'FFFFFF' } }
        ]
      : ws.label;
    slide.addText(labelText, {
      x: GRID_LEFT, y: rowY, w: ROW_LABEL_W, h: rowH,
      fontFace: FONT, fontSize: HEADER_SIZE, bold: true,
      color: 'FFFFFF', align: 'center', valign: 'middle', margin: 0
    });

    // Content cells for each week
    ws.cells.forEach((bullets, colIdx) => {
      const cellX = colX[colIdx];
      // Cell background
      slide.addShape(pptx.ShapeType.rect, {
        x: cellX, y: rowY, w: COL_W, h: rowH,
        fill: { color: MINT },
        line: { color: CELL_BORDER, width: 0.75 }
      });
      // Cell text
      const cellText = bullets.map(b => ({
        text: `● ${b}`,
        options: { fontFace: FONT, fontSize: CELL_SIZE, color: NAVY, breakType: 'none' }
      }));
      slide.addText(cellText, {
        x: cellX + CELL_INSET_X, y: rowY + 0.03,
        w: CELL_CONTENT_W, h: rowH - 0.06,
        valign: 'top', lineSpacingMultiple: CELL_LINE_SPACING, margin: 0
      });
    });
  });

  // Dashed divider lines (between workstream sections)
  const dividerYs = [2.218, 3.802];
  dividerYs.forEach(dy => {
    slide.addShape(pptx.ShapeType.line, {
      x: 0.539, y: dy, w: 8.96, h: 0,
      line: { color: DIVIDER_GREY, width: 0.75, dashType: 'dash' }
    });
  });

  // Deliverables row
  const delivY = 3.854;
  const delivH = 0.52;
  // Label
  slide.addText('Deliverables', {
    x: GRID_LEFT, y: delivY, w: ROW_LABEL_W, h: delivH,
    fontFace: FONT, fontSize: HEADER_SIZE, bold: true,
    color: DARK_TEAL, align: 'center', valign: 'middle', margin: 0
  });
  // Deliverable cells
  deliverables.forEach((items, colIdx) => {
    const cellX = colX[colIdx];
    slide.addShape(pptx.ShapeType.rect, {
      x: cellX, y: delivY, w: COL_W, h: delivH,
      fill: { color: MINT },
      line: { color: CELL_BORDER, width: 0.75 }
    });
    const cellText = items.map(item => ({
      text: `✓ ${item}`,
      options: { fontFace: FONT, fontSize: DELIV_SIZE, bold: true, color: NAVY, breakType: 'none' }
    }));
    slide.addText(cellText, {
      x: cellX + CELL_INSET_X, y: delivY + 0.03,
      w: CELL_CONTENT_W, h: delivH - 0.06,
      valign: 'top', lineSpacingMultiple: CELL_LINE_SPACING, margin: 0
    });
  });

  // Footnotes / source
  const footText = [];
  if (footnotes) footText.push({ text: footnotes, options: { fontFace: FONT, fontSize: FOOTNOTE_SIZE, color: SAND } });
  if (source) footText.push({ text: source, options: { fontFace: FONT, fontSize: FOOTNOTE_SIZE, italic: true, color: SAND } });
  if (footText.length) {
    slide.addText(footText, {
      x: 0.842, y: 5.086, w: 9.0, h: 0.2,
      valign: 'bottom', margin: 0
    });
  }

  // Bottom accent bar
  slide.addShape(pptx.ShapeType.rect, {
    x: 0, y: 5.525, w: SLIDE_W, h: 0.1,
    fill: { color: TEAL }
  });

  // Corner triangle
  slide.addShape(pptx.ShapeType.rtTriangle, {
    x: 9.118, y: -0.018, w: 0.865, h: 0.9,
    fill: { color: NAVY }, rotate: 270
  });

  // Page number badge
  slide.addShape(pptx.ShapeType.ellipse, {
    x: 9.589, y: 0.109, w: 0.3, h: 0.3,
    fill: { color: 'FFFFFF' }
  });
  slide.addText(String(slideNumber), {
    x: 9.589, y: 0.109, w: 0.3, h: 0.3,
    fontFace: 'Calibri', fontSize: 12, color: '000000',
    align: 'center', valign: 'middle', margin: 0
  });

  return slide;
}
```
