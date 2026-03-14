# Component: Objectives Slide (`objectives`)

The objectives slide. Same base structure as the situation slide (branded left panel + right content area) with a different content layout: bold teal action title followed by body paragraphs. No horizontal separator between title and body. Used for stating what the engagement will achieve.

---

> **Content guide:** See `content/objectives.md` for what to write on this slide.

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
| 5 | Text box | Section subtitle | 0.4 | 2.35 | 2.2 | 0.7 |
| 6 | Image | Logo/icon | 0.85 | 3.5 | 0.6 | 0.6 |
| 7 | Text box | Source citation | 3.4 | 5.25 | 6.2 | 0.2 |
| 8 | Rectangle | Bottom accent bar | 0.0 | 5.525 | 10.0 | 0.1 |
| 9 | Text box | Main body content | 3.833 | 0.772 | 5.752 | 1.894 |

Note: No corner triangle or page number badge on this slide. No horizontal separator between action title and body.

---

## Element details

### Element 1: Left panel background

| Property | Value |
|----------|-------|
| Shape | Rectangle |
| Fill | `#072E45` (Midnight Navy) |
| Border | None (width 0) |
| Text insets | 91,425 EMU all sides |
| Anchor | Center |

### Element 2: Decorative circle

| Property | Value |
|----------|-------|
| Shape | Ellipse |
| Fill | `#134F68` (Slate) |
| Opacity | 80% |
| Border | None |
| Position note | Partially off-slide to the left |

### Element 3: Section title

| Property | Value |
|----------|-------|
| Shape | Rectangle (transparent) |
| Fill | None (background) |
| Border | None |
| Text insets | 0 EMU all sides |
| Anchor | Center |
| **Text content** | `{{section_label}}` (e.g. "Objectives") |
| Font | Inter Tight |
| Size | 26pt |
| Weight | Bold |
| Colour | `#FFFFFF` |
| Alignment | Left |
| Language | en-GB |

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
| Fill | None (background) |
| Border | None |
| Text insets | 0 EMU all sides |
| Anchor | Center |
| **Text content** | `{{section_subtitle}}` (e.g. "How Turing Works will\nhelp the client achieve their goals") |
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

### Element 7: Source citation

| Property | Value |
|----------|-------|
| Shape | Rectangle (transparent) |
| Fill | None |
| Text insets | 0 EMU all sides |
| **Text content** | `{{source}}` (e.g. "Source: Turing Works statement of work hypothesis") |
| Font | Inter Tight |
| Size | 7.5pt |
| Weight | Regular |
| Style | Italic |
| Colour | `#B8AD90` (Sand) |
| Alignment | Left |
| Language | en-GB |

### Element 8: Bottom accent bar

| Property | Value |
|----------|-------|
| Shape | Rectangle |
| Fill | `#518C94` (Teal) |
| Border | None |
| Position note | Full width, near bottom edge |

### Element 9: Main body content

| Property | Value |
|----------|-------|
| Shape | Text box |
| Fill | None (background) |
| Border | None |
| Text insets | L/R: 68,575 EMU (0.075 in), T/B: 34,275 EMU (0.037 in) |
| Anchor | Top |
| Auto size | Shape to fit text |

**Text structure — bold action title paragraph followed by body paragraphs:**

**Paragraph 1 (action title):**
| Property | Value |
|----------|-------|
| **Text content** | `{{action_title}}` — conclusion statement, not a topic label |
| Font | Inter Tight |
| Size | 12pt |
| Weight | Bold |
| Colour | `#518C94` (Teal) |
| Alignment | Left |
| Language | en-GB |

**Paragraph 2:** Empty spacer

**Paragraph 3+ (body content):**
| Property | Value |
|----------|-------|
| **Text content** | `{{body_content}}` — supporting detail paragraphs |
| Font | Inter Tight |
| Size | 12pt |
| Weight | Regular |
| Colour | `#000000` (theme DARK_1) |
| Alignment | Left |
| Language | en-GB |

---

## Computed constants

| Constant | Value | How derived |
|----------|-------|-------------|
| Left panel width | 3.0 in | Width of Element 1 |
| Left panel inner margin | 0.4 in | x position of section title |
| Left panel text width | 2.2 in | Width of Elements 3 and 5 |
| Content area left edge | 3.833 in | x position of Element 9 |
| Content area width | 5.752 in | Width of Element 9 |
| Content area right edge | 9.585 in | x + w of Element 9 |
| Content text inset L/R | 0.075 in | Text inset of Element 9 |
| Content text inset T/B | 0.037 in | Text inset of Element 9 |
| Source citation y | 5.25 in | y position of Element 7 |
| Bottom bar y | 5.525 in | y position of Element 8 |
| Bottom bar height | 0.1 in | Height of Element 8 |
| Decorative circle opacity | 80% | Opacity of Element 2 |

---

## Differences from situation slide

| Property | Situation | Objectives |
|----------|-----------|------------|
| Section title size | 28pt | 26pt |
| Subtitle height | 0.6 in | 0.7 in |
| Decorative circle opacity | 100% | 80% |
| Content area x | 3.4 in | 3.833 in |
| Content area width | 6.2 in | 5.752 in |
| Content text insets | 0 EMU | L/R: 0.075 in, T/B: 0.037 in |
| Horizontal separator | Yes | No |
| Corner triangle + page badge | Yes | No |
| Body text colour | `#3A3A3A` | Theme DARK_1 (`#000000`) |
| Action title and body | Separate text boxes | Combined in single text box |
| Body auto size | None | Shape to fit text |
| Source y position | 5.15 in | 5.25 in |

---

## Template parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `section_label` | string | Yes | Section name on left panel (e.g. "Objectives") |
| `section_subtitle` | string | No | Short description below section title |
| `action_title` | string | Yes | Bold teal conclusion statement (first paragraph in body) |
| `body_content` | string[] | Yes | Array of body paragraphs below the action title |
| `source` | string | No | Source citation at bottom |
| `logo_path` | string | No | Path to logo/icon image for left panel |

---

## pptxgenjs code template

```javascript
function addObjectivesSlide(pptx, {
  sectionLabel,
  sectionSubtitle,
  actionTitle,
  bodyContent, // array of paragraph strings
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
  const CIRCLE_OPACITY = 80;

  // Section title
  const SECTION_TITLE_Y = 1.6;
  const SECTION_TITLE_H = 0.5;
  const SECTION_TITLE_FONT = 'Inter Tight';
  const SECTION_TITLE_SIZE = 26;
  const SECTION_TITLE_COLOR = 'FFFFFF';

  // Accent divider
  const DIVIDER_Y = 2.15;
  const DIVIDER_W = 0.9;
  const DIVIDER_H = 0.04;
  const ACCENT_COLOR = '518C94';

  // Section subtitle
  const SUBTITLE_Y = 2.35;
  const SUBTITLE_H = 0.7;
  const SUBTITLE_SIZE = 10.5;
  const SUBTITLE_COLOR = 'ADCFC9';

  // Content area
  const CONTENT_X = 3.833;
  const CONTENT_W = 5.752;
  const CONTENT_Y = 0.772;
  const CONTENT_INSET_LR = 0.075;
  const CONTENT_INSET_TB = 0.037;

  // Action title
  const ACTION_TITLE_SIZE = 12;
  const ACTION_TITLE_COLOR = '518C94';

  // Body text
  const BODY_SIZE = 12;
  const BODY_COLOR = '000000';

  // Source
  const SOURCE_X = 3.4;
  const SOURCE_Y = 5.25;
  const SOURCE_W = 6.2;
  const SOURCE_H = 0.2;
  const SOURCE_SIZE = 7.5;
  const SOURCE_COLOR = 'B8AD90';

  // Bottom bar
  const BOTTOM_BAR_Y = 5.525;
  const BOTTOM_BAR_H = 0.1;

  // --- Build slide ---
  const slide = pptx.addSlide();
  slide.background = { color: 'FFFFFF' };

  // 1. Left panel background
  slide.addShape(pptx.ShapeType.rect, {
    x: 0, y: 0, w: PANEL_W, h: SLIDE_H,
    fill: { color: PANEL_FILL }
  });

  // 2. Decorative circle (80% opacity)
  slide.addShape(pptx.ShapeType.ellipse, {
    x: CIRCLE_X, y: CIRCLE_Y, w: CIRCLE_SIZE, h: CIRCLE_SIZE,
    fill: { color: CIRCLE_FILL, transparency: 100 - CIRCLE_OPACITY }
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

  // 9. Main body content (action title + body paragraphs in single text box)
  const textRows = [
    { text: actionTitle, options: {
      fontFace: SECTION_TITLE_FONT, fontSize: ACTION_TITLE_SIZE,
      bold: true, color: ACTION_TITLE_COLOR, breakType: 'none'
    }},
    { text: '', options: { fontSize: ACTION_TITLE_SIZE, breakType: 'none' }}, // spacer
    ...bodyContent.map(para => ({
      text: para, options: {
        fontFace: SECTION_TITLE_FONT, fontSize: BODY_SIZE,
        color: BODY_COLOR, breakType: 'none'
      }
    }))
  ];

  slide.addText(textRows, {
    x: CONTENT_X, y: CONTENT_Y, w: CONTENT_W,
    margin: [CONTENT_INSET_TB * 72, CONTENT_INSET_LR * 72,
             CONTENT_INSET_TB * 72, CONTENT_INSET_LR * 72],
    valign: 'top',
    autoFit: true
  });

  // 7. Source citation
  if (source) {
    slide.addText(source, {
      x: SOURCE_X, y: SOURCE_Y, w: SOURCE_W, h: SOURCE_H,
      fontFace: SECTION_TITLE_FONT,
      fontSize: SOURCE_SIZE,
      italic: true,
      color: SOURCE_COLOR,
      align: 'left',
      margin: 0
    });
  }

  // 8. Bottom accent bar
  slide.addShape(pptx.ShapeType.rect, {
    x: 0, y: BOTTOM_BAR_Y, w: SLIDE_W, h: BOTTOM_BAR_H,
    fill: { color: ACCENT_COLOR }
  });

  return slide;
}
```
