---
name: proposal-letter
description: Convert Turing Works slide decks, proposals, and engagement scopes into clean Word document (.docx) letters in BCG proposal letter format. Use this skill whenever Alasdair asks to turn a deck into a Word doc, create a proposal letter, produce a written version of a presentation, make a "letter format" or "document version" of slides, or generate a client-facing proposal as a .docx. Also trigger when he says "BCG format", "letter version", "word version of the deck", "make this a doc", or references converting any proposal or pitch content into a written document. This skill supersedes the generic docx skill for any Turing Works client proposal output.
---

# Proposal Letter — BCG-Style Word Document from Slide Content

This skill converts Turing Works slide decks and proposal content into professional Word documents that follow the BCG proposal letter format: a clean, black-and-white document with bold numbered section headers, tight bullet points, and consistent 11pt Arial throughout.

The source material is typically a .pptx presentation (or PDF of one). The output is a .docx that a client could read as a standalone document — every section of the deck becomes a numbered section in the letter.

---

## FORMAT RULES

These rules are non-negotiable. They define the BCG letter aesthetic.

### Typography
- **Font**: Arial, 11pt (`size: 22` in docx-js) for everything — body, bullets, bold headers, table cells
- **Source/citation lines**: 9pt Arial, italic, grey (`color: "666666"`) — the only exception to 11pt
- **No heading styles**: Never use `HeadingLevel.HEADING_1` or any Word heading style. Section headers are just bold text runs in a normal paragraph
- **No mixed font sizes**: Body text, bullets, sub-headers, table body cells — all 11pt

### Spacing
- **Line spacing**: 1.15 (`line: 276` in docx-js)
- **After paragraph**: 120 twips (`after: 120`) — uniform for all paragraphs and bullets
- **Before section headers**: 240 twips (`before: 240`) to create visual separation
- **No extra spacing between bullets**: Every bullet gets the same `{ line: 276, before: 0, after: 120 }` — never add extra gaps
- **Table cell paragraphs**: Tight spacing `{ line: 276, before: 0, after: 0 }` to keep tables compact

### Structure
- **Date**: First line, plain text (e.g. "20 March 2026")
- **Re: line**: Bold, states the engagement and client name
- **Numbered sections**: Bold text like "**1. Section name**" — these are normal paragraphs with bold runs, not heading styles
- **Sub-headers within sections**: Bold text (e.g. "**Part A — Start Tue 24th March**") — again, just bold runs
- **Bullets**: Proper Word numbering with `LevelFormat.BULLET`, indented at 360 twips. Never use unicode bullet characters directly
- **Numbered lists**: `LevelFormat.DECIMAL` for ordered items (e.g. objectives 1, 2, 3)
- **Sub-bullets**: Level 1 bullets indented at 720 twips with open circle character
- **Source lines**: Italic 9pt grey, attributed to the discovery call or engagement source
- **Sign-off**: Addresses client stakeholders by name, "Yours sincerely," then partners' names
- **No headers/footers** unless specifically requested

### Tables
- **Border**: Light grey `{ style: BorderStyle.SINGLE, size: 1, color: "CCCCCC" }`
- **Header row**: Dark fill `#2D3E50`, white bold text, 10pt
- **Body cells**: 10pt Arial (`size: 20`), tight internal spacing
- **Module/label column**: Light grey fill `#F2F2F2` for visual anchoring
- **Deliverables row**: Light green fill `#EAF2EA` with tick marks (`✓`)
- **Cell margins**: `{ top: 40, bottom: 40, left: 80, right: 80 }`
- **Table width**: Full content width — 9026 DXA for A4 with 1" margins

### Page Setup
- **Paper**: A4 (11906 × 16838 DXA)
- **Margins**: 1 inch all sides (1440 DXA)
- **Black and white only**: No brand colours in body text. Tables may use the dark header fill and light row fills described above

---

## SECTION MAPPING

When converting a slide deck to this format, map slides to numbered sections. The typical Turing Works proposal deck maps as follows — adapt section names and ordering to match whatever deck is provided:

| Deck section | Letter section | Notes |
|---|---|---|
| Title slide | Date + Re: line | Extract client name, engagement title, date |
| Situation / Context | "Our understanding of [Client]'s context" | Preserve bullet structure and bold emphasis from slides |
| Objectives | "Objectives" | Use numbered list for each objective; bold the objective name, plain text for description |
| Proposal summary | "Proposal" | Include the objectives-to-deliverables mapping table |
| Deliverables | "Deliverables" | Sub-headers for each deliverable stream with bullets |
| Workplan (phased) | "Phase 1 Workplan" or similar | Part A / Part B structure with bullets; include deliverables callout |
| Workplan (weekly) | "Full workplan" | Convert to a table (Module × Week grid) |
| Resourcing / project team | "Phase N resourcing, workplan, and project team" or similar | **Critical — tied to contract and fee negotiations. Never omit or summarise.** Structure: (1) prose paragraph on why the team is needed and overall engagement shape; (2) prose paragraph naming who leads and who supports; (3) bold label "Proposed resourcing:" followed by bullets breaking down team by week/phase (e.g. "Weeks 1–2: X and Y ramp up…", "Weeks 3–10: full team of N"); (4) prose paragraphs on support model (sessions per week, review cadence, continuity rationale). Preserve all names, week ranges, and staffing numbers exactly from the source |
| Workshop structure | "Workshop structure" | Goal / Team / Duration as bold-label bullets; list known issues |
| Ways of working | "How we will work together" | Analysis → Solution → Implementation with bullets under each |
| Why us | "Why Turing Works is the right partner" | Bold capability name + plain description bullets |
| Team | "Project team" | Table with Leadership / Sponsor / Project Team columns |
| Case studies | "Previous experience" | Bold case name, then one-paragraph summary per case |
| Closing | Sign-off paragraph | Address stakeholders by first name |

Not every deck will have all these sections. Some decks will have sections not listed here. Use judgment — the principle is that every substantive slide becomes a section, and the letter should be readable as a standalone document.

**Numbering rule**: Section numbers must be sequential with no gaps (1, 2, 3, 4, 5, 6…). Never skip numbers — if you map 10 sections, they are numbered 1–10 regardless of how slides are numbered in the source deck.

**Deliverables/workplan alignment rule**: The deliverables listed in the Deliverables section must exactly match what is delivered in the Workplan. If the engagement is Phase 1 only, both sections must reflect Phase 1 deliverables only — do not carry over multi-phase deliverables from the deck if the scope is narrower. Cross-check before writing.

---

## CONTENT RULES

### Fidelity to source
- Use the exact words from the slides wherever possible. The letter should be as accurate a reflection of the deck as possible — not a rewrite
- Preserve the bold/plain emphasis pattern from slides: if a phrase is bolded on a slide, bold it in the letter
- Include all source citations from the slides (e.g. "Source: Discovery call with Noel Foong...")
- Preserve slide numbering conventions (e.g. if objectives are numbered 1, 2, 3 on the slide, use the same numbering)

### What to adapt
- Slides often use fragments; in the letter, ensure each bullet is a grammatically complete thought where needed, but don't over-edit — preserve the concise slide style
- **Resourcing and project team sections**: write as full prose paragraphs, not bullets. These sections describe team composition, ways of working, and scheduling in narrative form — convert slide fragments into complete sentences and flowing paragraphs
- Slide action titles become section context sentences or bold sub-headers
- Convert visual elements (process flows, team grids) into tables
- The "To discuss" labels from slides can be noted as italicised parentheticals

### What to omit
- Appendix slides (unless explicitly requested)
- Decorative elements, icons, images (unless the user asks to include them)
- Slide numbers and section markers (replaced by the numbered section structure)
- **Next steps slides** — always exclude. The proposal letter ends with the sign-off paragraph

---

## IMPLEMENTATION

Use the docx skill's `docx-js` approach (Node.js with the `docx` npm package). The key code patterns:

### Numbering config
```javascript
const numbering = {
  config: [
    {
      reference: "b1",
      levels: [{
        level: 0, format: LevelFormat.BULLET, text: "\u2022",
        alignment: AlignmentType.LEFT,
        style: { paragraph: { indent: { left: 360, hanging: 360 } } }
      }, {
        level: 1, format: LevelFormat.BULLET, text: "\u25CB",
        alignment: AlignmentType.LEFT,
        style: { paragraph: { indent: { left: 720, hanging: 360 } } }
      }]
    },
    {
      reference: "n1",
      levels: [{
        level: 0, format: LevelFormat.DECIMAL, text: "%1.",
        alignment: AlignmentType.LEFT,
        style: { paragraph: { indent: { left: 360, hanging: 360 } } }
      }]
    }
  ]
};
```

### Spacing constants
```javascript
const STD = { line: 276, before: 0, after: 120 };
const SECTION_BEFORE = { line: 276, before: 240, after: 120 };
const TIGHT = { line: 276, before: 0, after: 0 }; // for table cells
```

### Helper functions
```javascript
function t(text) { return new TextRun({ text, font: "Arial", size: 22 }); }
function b(text) { return new TextRun({ text, bold: true, font: "Arial", size: 22 }); }
function it(text) { return new TextRun({ text, italics: true, font: "Arial", size: 18, color: "666666" }); }

const bullet = (children) => new Paragraph({ numbering: { reference: "b1", level: 0 }, spacing: STD, children });
const bullet2 = (children) => new Paragraph({ numbering: { reference: "b1", level: 1 }, spacing: STD, children });
const num = (children) => new Paragraph({ numbering: { reference: "n1", level: 0 }, spacing: STD, children });
const para = (children, spacing = STD) => new Paragraph({ spacing, children });
const sectionHead = (text) => new Paragraph({ spacing: SECTION_BEFORE, children: [b(text)] });
```

### Document setup
```javascript
const doc = new Document({
  numbering,
  styles: {
    default: {
      document: {
        run: { font: "Arial", size: 22 },
        paragraph: { spacing: { line: 276, before: 0, after: 120 } }
      }
    }
  },
  sections: [{
    properties: {
      page: {
        size: { width: 11906, height: 16838 }, // A4
        margin: { top: 1440, right: 1440, bottom: 1440, left: 1440 }
      }
    },
    children: content
  }]
});
```

### Table patterns
```javascript
// Header cell
new TableCell({
  borders: tBorders,
  width: { size: colWidth, type: WidthType.DXA },
  shading: { fill: "2D3E50", type: ShadingType.CLEAR },
  margins: { top: 40, bottom: 40, left: 80, right: 80 },
  children: [new Paragraph({ children: [
    new TextRun({ text: "Header", bold: true, font: "Arial", size: 20, color: "FFFFFF" })
  ] })]
})

// Body cell
new TableCell({
  borders: tBorders,
  width: { size: colWidth, type: WidthType.DXA },
  margins: { top: 40, bottom: 40, left: 80, right: 80 },
  children: [new Paragraph({ spacing: TIGHT, children: [
    new TextRun({ text: "Content", font: "Arial", size: 20 })
  ] })]
})
```

---

## REFERENCE TEMPLATE

A sanitized reference template is available at `assets/template.docx`. Use this to verify formatting, spacing, and structure — it shows the exact layout expected with all client-specific content replaced by `[PLACEHOLDER]` values.

---

## VALIDATION

After generating the .docx file, always run:
```bash
python scripts/office/validate.py output.docx
```

---

## PRE-FLIGHT CHECKLIST

Before delivering the document:

- [ ] Date is correct and matches user's instruction
- [ ] Re: line names the client and engagement
- [ ] All sections are bold numbered text (no Word heading styles)
- [ ] Every paragraph is 11pt Arial — no size variation except source lines (9pt)
- [ ] Spacing is uniform: 1.15 line, 120 twips after, no extra gaps between bullets
- [ ] Tables use dark header / light body pattern with 10pt text
- [ ] Source citations preserved from the original deck
- [ ] Sign-off addresses stakeholders by first name
- [ ] No brand colours in body text (black and white only)
- [ ] Appendix slides and Next Steps slides excluded
- [ ] Section numbers are sequential with no gaps
- [ ] Deliverables section matches Workplan scope exactly (Phase 1 only if Phase 1 only)
- [ ] Resourcing section included with full team names, week ranges, staffing numbers, and support model
- [ ] File validates with no errors
