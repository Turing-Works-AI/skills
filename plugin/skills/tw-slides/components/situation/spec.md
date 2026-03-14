# Component: Situation Slide (`situation`)

The base situation/context slide. Features a branded left panel (section title, subtitle, accent divider, logo) and a right content area (action title, separator, body text, source citation). Other element types (boxes, metrics, process flows, etc.) compose onto this base layout.

---

> **Content guide:** See `content/situation.md` for what to write on this slide.

---

## Slide properties

| Property | Value |
|----------|-------|
| Width | 10.0 in |
| Height | 5.625 in |
| Background | `#FFFFFF` |
| Aspect ratio | 16:9 |

---

## Element inventory

| # | Element type | Name/role | x (in) | y (in) | w (in) | h (in) |
|---|-------------|-----------|--------|--------|--------|--------|
| 1 | Rectangle | Left panel background | 0.0 | 0.0 | 3.0 | 5.625 |
| 2 | Ellipse | Decorative circle (bottom-left) | -0.6 | 3.6 | 2.6 | 2.6 |
| 3 | Text box | Section title | 0.4 | 1.6 | 2.2 | 0.5 |
| 4 | Rectangle | Accent divider line | 0.4 | 2.15 | 0.9 | 0.04 |
| 5 | Text box | Section subtitle | 0.4 | 2.35 | 2.2 | 0.6 |
| 6 | Image | Logo/icon | 0.85 | 3.5 | 0.6 | 0.6 |
| 7 | Text box | Main statement (action title) | 3.4 | 0.35 | 6.2 | 0.6 |
| 8 | Rectangle | Horizontal separator | 3.4 | 1.05 | 6.2 | 0.0098 |
| 9 | Text box | Body content | 3.4 | 1.2025 | 6.2 | 0.85 |
| 10 | Text box | Source citation | 3.4 | 5.15 | 6.2 | 0.25 |
| 11 | Rectangle | Bottom accent bar | 0.0 | 5.525 | 10.0 | 0.1 |
| 12 | Triangle | Corner triangle (top-right) | 9.118 | -0.018 | 0.865 | 0.9 |
| 13 | Ellipse | Page number badge | 9.589 | 0.109 | 0.3 | 0.3 |

---

## Element details

### Element 1: Left panel background

| Property | Value |
|----------|-------|
| Shape | Rectangle |
| Fill | `#072E45` (Midnight Navy) |
| Border | None |
| Text insets | 91425 EMU all sides |
| Anchor | Center |

### Element 2: Decorative circle

| Property | Value |
|----------|-------|
| Shape | Ellipse |
| Fill | `#134F68` (Slate) |
| Border | None |
| Position note | Partially off-slide to the left |

### Element 3: Section title

| Property | Value |
|----------|-------|
| Shape | Rectangle (transparent) |
| Fill | None |
| Border | None |
| Text insets | 0 EMU all sides |
| **Text content** | `{{section_label}}` (e.g. "Situation", "Objectives", "Proposal") |
| Font | Inter Tight |
| Size | 28pt |
| Weight | Bold |
| Colour | `#FFFFFF` |
| Alignment | Left |
| Language | en-GB |
| Cap | None |

### Element 4: Accent divider line

| Property | Value |
|----------|-------|
| Shape | Rectangle (thin) |
| Fill | `#518C94` (Teal) |
| Border | None |

### Element 5: Section subtitle

| Property | Value |
|----------|-------|
| Shape | Rectangle (transparent) |
| Fill | None |
| Border | None |
| Text insets | 0 EMU all sides |
| **Text content** | `{{section_subtitle}}` (e.g. "Understanding the client's\ncontext and AI ambitions") |
| Font | Inter Tight |
| Size | 10.5pt |
| Weight | Regular |
| Colour | `#ADCFC9` (Aqua) |
| Alignment | Left |
| Line spacing | 130% |
| Language | en-GB |

### Element 6: Logo/icon

| Property | Value |
|----------|-------|
| Type | Picture |
| Size | 0.6 x 0.6 in |
| Format | PNG |
| Content | Turing Works icon (or client logo) |

### Element 7: Main statement (action title)

| Property | Value |
|----------|-------|
| Shape | Rectangle (transparent) |
| Fill | None |
| Border | None |
| Text insets | 0 EMU all sides |
| **Text content** | `{{action_title}}` — a conclusion statement, not a topic label |
| Font | Inter Tight |
| Size | 12pt |
| Weight | Bold |
| Colour | `#518C94` (Teal) |
| Alignment | Left |
| Line spacing | 130% |
| Language | en-GB |
| Notes | Supports selective bold within runs for emphasis |

### Element 8: Horizontal separator

| Property | Value |
|----------|-------|
| Shape | Rectangle (hairline — 0.0098 in tall) |
| Fill | `#E8E8E4` (Light Stone) |
| Border | None |

### Element 9: Body content

| Property | Value |
|----------|-------|
| Shape | Rectangle (transparent) |
| Fill | None |
| Border | None |
| Text insets | 0 EMU all sides |
| **Text content** | `{{body_content}}` — paragraph text with selective bold for key terms |
| Font | Inter Tight |
| Size | 12pt |
| Weight | Regular (with selective bold on key terms) |
| Colour | `#3A3A3A` (Dark Grey) |
| Alignment | Left |
| Line spacing | 135% |
| Language | en-GB |

### Element 10: Source citation

| Property | Value |
|----------|-------|
| Shape | Rectangle (transparent) |
| Fill | None |
| Border | None |
| Text insets | 0 EMU all sides |
| **Text content** | `{{source}}` (e.g. "Source: Initial discussions with client stakeholder (Name)") |
| Font | Inter Tight |
| Size | 7.5pt |
| Weight | Regular |
| Style | Italic |
| Colour | `#B8AD90` (Sand) |
| Alignment | Left |
| Language | en-GB |

### Element 11: Bottom accent bar

| Property | Value |
|----------|-------|
| Shape | Rectangle |
| Fill | `#518C94` (Teal) |
| Border | None |
| Position note | Full width, near bottom edge |

### Element 12: Corner triangle (page number background)

| Property | Value |
|----------|-------|
| Shape | Triangle (right triangle, adj = 100000) |
| Fill | `#072E45` (Midnight Navy) |
| Border | None |
| Rotation | 270 degrees |
| Text insets | 68575 / 34275 / 68575 / 34275 EMU (L/T/R/B) |

### Element 13: Page number badge

| Property | Value |
|----------|-------|
| Shape | Ellipse |
| Fill | `#FFFFFF` (White, theme LIGHT_1) |
| Border | None |
| Text insets | 0 EMU all sides |
| **Text content** | `{{slide_number}}` |
| Font | Calibri |
| Size | 12pt |
| Weight | Regular |
| Colour | `#000000` (Black, theme DARK_1) |
| Alignment | Centre |
| Language | en-GB |

---

## Computed constants

| Constant | Value | How derived |
|----------|-------|-------------|
| Left panel width | 3.0 in | Width of Element 1 |
| Content area left edge | 3.4 in | x position of Elements 7–10 |
| Content area right edge | 9.6 in | x + w of Elements 7–10 (3.4 + 6.2) |
| Content area width | 6.2 in | Width of Elements 7–10 |
| Right margin | 0.4 in | Slide width − content right edge (10.0 − 9.6) |
| Left panel inner margin | 0.4 in | x position of section title (Element 3) |
| Left panel text width | 2.2 in | Width of Elements 3 and 5 |
| Gap between panel and content | 0.4 in | Content left edge − panel width (3.4 − 3.0) |
| Action title top | 0.35 in | y position of Element 7 |
| Separator y position | 1.05 in | y position of Element 8 |
| Body content top | 1.2025 in | y position of Element 9 |
| Source citation y | 5.15 in | y position of Element 10 |
| Bottom bar y | 5.525 in | y position of Element 11 |
| Bottom bar height | 0.1 in | Height of Element 11 |
| Page number badge x | 9.589 in | x position of Element 13 |
| Page number badge y | 0.109 in | y position of Element 13 |
| Page number badge diameter | 0.3 in | Width/height of Element 13 |

---

## Template parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `section_label` | string | Yes | Section name displayed on left panel (e.g. "Situation") |
| `section_subtitle` | string | No | Short description below section title on left panel |
| `action_title` | string | Yes | Conclusion statement for the slide (bold teal, top of content area) |
| `body_content` | string | Yes | Main paragraph content with optional `**bold**` markers for key terms |
| `source` | string | No | Source citation at bottom of content area |
| `slide_number` | number | Yes | Page number displayed in top-right badge |
| `logo_path` | string | No | Path to logo/icon image for left panel |

---

## pptxgenjs code template

```javascript
function addContentOneColSlide(pptx, {
  slideNumber,
  sectionLabel,
  sectionSubtitle,
  actionTitle,
  bodyContent,
  source,
  logoPath
}) {
  // --- Constants (extracted from spec) ---
  const SLIDE_W = 10.0;
  const SLIDE_H = 5.625;

  // Left panel
  const PANEL_W = 3.0;
  const PANEL_FILL = '072E45';
  const PANEL_MARGIN = 0.4;
  const PANEL_TEXT_W = 2.2;

  // Decorative circle
  const CIRCLE_X = -0.6;
  const CIRCLE_Y = 3.6;
  const CIRCLE_SIZE = 2.6;
  const CIRCLE_FILL = '134F68';

  // Section title
  const SECTION_TITLE_Y = 1.6;
  const SECTION_TITLE_H = 0.5;
  const SECTION_TITLE_FONT = 'Inter Tight';
  const SECTION_TITLE_SIZE = 28;
  const SECTION_TITLE_COLOR = 'FFFFFF';

  // Accent divider
  const DIVIDER_Y = 2.15;
  const DIVIDER_W = 0.9;
  const DIVIDER_H = 0.04;
  const ACCENT_COLOR = '518C94';

  // Section subtitle
  const SUBTITLE_Y = 2.35;
  const SUBTITLE_H = 0.6;
  const SUBTITLE_SIZE = 10.5;
  const SUBTITLE_COLOR = 'ADCFC9';

  // Content area
  const CONTENT_X = 3.4;
  const CONTENT_W = 6.2;

  // Action title
  const ACTION_TITLE_Y = 0.35;
  const ACTION_TITLE_H = 0.6;
  const ACTION_TITLE_SIZE = 12;
  const ACTION_TITLE_COLOR = '518C94';

  // Separator
  const SEPARATOR_Y = 1.05;
  const SEPARATOR_H = 0.0098;
  const SEPARATOR_COLOR = 'E8E8E4';

  // Body
  const BODY_Y = 1.2025;
  const BODY_H = 0.85;
  const BODY_SIZE = 12;
  const BODY_COLOR = '3A3A3A';

  // Source
  const SOURCE_Y = 5.15;
  const SOURCE_H = 0.25;
  const SOURCE_SIZE = 7.5;
  const SOURCE_COLOR = 'B8AD90';

  // Bottom bar
  const BOTTOM_BAR_Y = 5.525;
  const BOTTOM_BAR_H = 0.1;

  // Corner triangle
  const TRIANGLE_X = 9.118;
  const TRIANGLE_Y = -0.018;
  const TRIANGLE_W = 0.865;
  const TRIANGLE_H = 0.9;

  // Page number badge
  const BADGE_X = 9.589;
  const BADGE_Y = 0.109;
  const BADGE_SIZE = 0.3;

  // --- Build slide ---
  const slide = pptx.addSlide();
  slide.background = { color: 'FFFFFF' };

  // 1. Left panel background
  slide.addShape(pptx.ShapeType.rect, {
    x: 0, y: 0, w: PANEL_W, h: SLIDE_H,
    fill: { color: PANEL_FILL }
  });

  // 2. Decorative circle
  slide.addShape(pptx.ShapeType.ellipse, {
    x: CIRCLE_X, y: CIRCLE_Y, w: CIRCLE_SIZE, h: CIRCLE_SIZE,
    fill: { color: CIRCLE_FILL }
  });

  // 3. Section title
  slide.addText(sectionLabel, {
    x: PANEL_MARGIN, y: SECTION_TITLE_Y, w: PANEL_TEXT_W, h: SECTION_TITLE_H,
    fontFace: SECTION_TITLE_FONT,
    fontSize: SECTION_TITLE_SIZE,
    bold: true,
    color: SECTION_TITLE_COLOR,
    align: 'left',
    margin: 0
  });

  // 4. Accent divider
  slide.addShape(pptx.ShapeType.rect, {
    x: PANEL_MARGIN, y: DIVIDER_Y, w: DIVIDER_W, h: DIVIDER_H,
    fill: { color: ACCENT_COLOR }
  });

  // 5. Section subtitle
  if (sectionSubtitle) {
    slide.addText(sectionSubtitle, {
      x: PANEL_MARGIN, y: SUBTITLE_Y, w: PANEL_TEXT_W, h: SUBTITLE_H,
      fontFace: SECTION_TITLE_FONT,
      fontSize: SUBTITLE_SIZE,
      color: SUBTITLE_COLOR,
      align: 'left',
      lineSpacingMultiple: 1.3,
      margin: 0
    });
  }

  // 6. Logo/icon
  if (logoPath) {
    slide.addImage({
      path: logoPath,
      x: 0.85, y: 3.5, w: 0.6, h: 0.6
    });
  }

  // 7. Action title (main statement)
  slide.addText(actionTitle, {
    x: CONTENT_X, y: ACTION_TITLE_Y, w: CONTENT_W, h: ACTION_TITLE_H,
    fontFace: SECTION_TITLE_FONT,
    fontSize: ACTION_TITLE_SIZE,
    bold: true,
    color: ACTION_TITLE_COLOR,
    align: 'left',
    lineSpacingMultiple: 1.3,
    margin: 0
  });

  // 8. Horizontal separator
  slide.addShape(pptx.ShapeType.rect, {
    x: CONTENT_X, y: SEPARATOR_Y, w: CONTENT_W, h: SEPARATOR_H,
    fill: { color: SEPARATOR_COLOR }
  });

  // 9. Body content
  slide.addText(bodyContent, {
    x: CONTENT_X, y: BODY_Y, w: CONTENT_W, h: BODY_H,
    fontFace: SECTION_TITLE_FONT,
    fontSize: BODY_SIZE,
    color: BODY_COLOR,
    align: 'left',
    lineSpacingMultiple: 1.35,
    margin: 0
  });

  // 10. Source citation
  if (source) {
    slide.addText(source, {
      x: CONTENT_X, y: SOURCE_Y, w: CONTENT_W, h: SOURCE_H,
      fontFace: SECTION_TITLE_FONT,
      fontSize: SOURCE_SIZE,
      italic: true,
      color: SOURCE_COLOR,
      align: 'left',
      margin: 0
    });
  }

  // 11. Bottom accent bar
  slide.addShape(pptx.ShapeType.rect, {
    x: 0, y: BOTTOM_BAR_Y, w: SLIDE_W, h: BOTTOM_BAR_H,
    fill: { color: ACCENT_COLOR }
  });

  // 12. Corner triangle
  slide.addShape(pptx.ShapeType.rtTriangle, {
    x: TRIANGLE_X, y: TRIANGLE_Y, w: TRIANGLE_W, h: TRIANGLE_H,
    fill: { color: PANEL_FILL },
    rotate: 270
  });

  // 13. Page number badge
  slide.addShape(pptx.ShapeType.ellipse, {
    x: BADGE_X, y: BADGE_Y, w: BADGE_SIZE, h: BADGE_SIZE,
    fill: { color: 'FFFFFF' }
  });
  slide.addText(String(slideNumber), {
    x: BADGE_X, y: BADGE_Y, w: BADGE_SIZE, h: BADGE_SIZE,
    fontFace: 'Calibri',
    fontSize: 12,
    color: '000000',
    align: 'center',
    valign: 'middle',
    margin: 0
  });

  return slide;
}
```
