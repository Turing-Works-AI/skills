---
name: tw-data-access-request
description: Generate Turing Works data access request documents for new client engagements. Use this skill whenever Alasdair asks to create a data access request, tool access request, onboarding request, access checklist, or any document requesting credentials, system access, or tool permissions from a client. Also trigger when he says "DAR", "data access", "access request", "onboarding doc", "what access do we need", "tool access", or references setting up access for a new engagement. This skill uses the existing branded template (landscape, 6-column table with grey section rows and dark header) and rewrites the body content for the new client. Always use this skill instead of creating a data access document from scratch.
---

# Data Access Request — Turing Works Client Onboarding Document

This skill produces a branded data access request document for a new Turing Works client engagement. The output is a .docx that preserves the exact formatting of the original template (landscape A4, tight margins, 6-column table, "Confidential | Turing Works" header) with body content rewritten for the new client.

---

## APPROACH

Edit the template, don't create from scratch. The template at `assets/template.docx` defines the page layout, header, table formatting, column widths, and border styles. The workflow is:

1. Unpack the template using `scripts/office/unpack.py`
2. Rewrite the body XML in `word/document.xml` with new content
3. Add any new hyperlink relationships to `word/_rels/document.xml.rels`
4. Repack using `scripts/office/pack.py`

This preserves the landscape orientation, margins, embedded fonts, header, and table style exactly.

---

## TEMPLATE STRUCTURE

The template has these fixed properties — never change them:

### Page Setup
- **Orientation**: Landscape
- **Page size**: `w:h="12240" w:w="15840"` (US Letter landscape)
- **Margins**: ~567 DXA all sides (tight, to fit the wide table)
- **Header**: "Confidential |" in red bold + "Turing Works" in black bold, right-aligned

### Table Layout
- **Total width**: 14670 DXA
- **Column grid** (6 columns):
  - ID: 795 DXA
  - Category: 1995 DXA
  - Item: 2490 DXA
  - Access Level: 2325 DXA
  - Rationale: 5415 DXA
  - Owner: 1650 DXA
- **Borders**: Black, single, size 8
- **Cell margins**: 100 DXA all sides
- **Header row**: Fill `666666`, white bold text, `tblHeader` enabled
- **Section rows**: Fill `f3f3f3`, bold text in ID and Category columns, remaining cells empty
- **Data rows**: Fill `auto` (white), plain text except Category column which is bold

### Header Columns
The template uses these column headers. The fourth column was "Granularity / Period" in the ARM original — rename it to "Access Level" for most engagements, but adapt to what makes sense for the specific request.

| Column | Header | Content guidance |
|---|---|---|
| ID | ID | Section: `1.0`, `2.0` etc. Rows: `1.1`, `1.2` etc. |
| Category | Category | Bold. The system/tool name (e.g. "Omni Analytics", "Google Workspace") |
| Item | Item | What specifically is needed (account, folder, API key, etc.) |
| Access Level | Access Level | Read / Write / Admin / Guest — be specific |
| Rationale | Rationale | Why TW needs this for the engagement. Reference proposal deliverables |
| Owner | Owner | Who at the client should action this |

---

## BODY CONTENT PATTERN

The document body (before the table) follows this pattern:

### Title
Bold, 14pt (`w:sz="28"`): `Request for Data & Tool Access | [Short engagement name]`

### Objective
Bold label + plain text: `Objective: To secure all necessary tool access and permissions required so Turing Works can commence [Phase/work description] on [target start date].`

### Instructions
Bold label + plain text with hyperlinked email addresses: `Instructions: Please review the list below and grant access to both: alasdair@turingworks.ai and james@turingworks.ai`

The hyperlinks use `rId6` (Alasdair — already in template) and `rId8` (James — add to rels). Style: Roboto Mono font, colour `1155cc`, underlined.

### Table
See template structure above. Group rows into logical sections:

**Typical sections for a consulting engagement:**
- **1.0 System Access** — client tools TW needs to use (analytics, ERP, payment systems, etc.)
- **2.0 Google Workspace** — email accounts and Drive access within client domain
- **3.0 Collaboration & Documentation** — Notion, Slack, project management tools

Adapt sections to the engagement. An automation engagement might have different sections than a consulting one.

---

## XML PATTERNS

These patterns match the template exactly. Use them when constructing the replacement XML.

### Paragraph attributes
```xml
w:rsidR="00000000" w:rsidDel="00000000" w:rsidP="00000000" w:rsidRDefault="00000000" w:rsidRPr="00000000"
```
Each paragraph needs a unique `w14:paraId` (8-digit hex, sequential from `00000001`).

### Text run (plain)
```xml
<w:r>
  <w:rPr><w:rtl w:val="0"/></w:rPr>
  <w:t xml:space="preserve">Text here</w:t>
</w:r>
```

### Text run (bold)
```xml
<w:r>
  <w:rPr>
    <w:b w:val="1"/><w:bCs w:val="1"/>
    <w:rtl w:val="0"/>
  </w:rPr>
  <w:t xml:space="preserve">Bold text</w:t>
</w:r>
```

### Hyperlink
```xml
<w:hyperlink r:id="rId6">
  <w:r>
    <w:rPr>
      <w:rFonts w:ascii="Roboto Mono" w:cs="Roboto Mono" w:eastAsia="Roboto Mono" w:hAnsi="Roboto Mono"/>
      <w:color w:val="1155cc"/>
      <w:u w:val="single"/>
      <w:rtl w:val="0"/>
    </w:rPr>
    <w:t xml:space="preserve">alasdair@turingworks.ai</w:t>
  </w:r>
</w:hyperlink>
```

### Header cell (fill 666666, white bold text)
```xml
<w:tc>
  <w:tcPr>
    <w:shd w:fill="666666" w:val="clear"/>
    <w:tcMar>
      <w:top w:w="100.0" w:type="dxa"/>
      <w:left w:w="100.0" w:type="dxa"/>
      <w:bottom w:w="100.0" w:type="dxa"/>
      <w:right w:w="100.0" w:type="dxa"/>
    </w:tcMar>
    <w:vAlign w:val="top"/>
  </w:tcPr>
  <w:p ...>
    <w:pPr><w:jc w:val="left"/><w:rPr><w:b w:val="1"/><w:bCs w:val="1"/><w:color w:val="ffffff"/></w:rPr></w:pPr>
    <w:r><w:rPr><w:b w:val="1"/><w:bCs w:val="1"/><w:color w:val="ffffff"/><w:rtl w:val="0"/></w:rPr><w:t xml:space="preserve">Header Text</w:t></w:r>
  </w:p>
</w:tc>
```

### Section row (fill f3f3f3, bold ID + Category)
All 6 cells get `f3f3f3` fill. ID and Category cells have bold text. Remaining 4 cells are empty (contain an empty run).

### Data row (fill auto, Category bold)
All 6 cells get `auto` fill. Category cell text is bold. All other cells are plain text.

---

## IMPLEMENTATION STEPS

### Step 1: Unpack
```bash
python scripts/office/unpack.py <skill_path>/assets/template.docx /home/claude/dar_unpacked/
```

### Step 2: Build replacement body XML
Write a Python script that:
1. Reads the original `document.xml`
2. Extracts the opening (everything up to and including `<w:body>`) and closing (`<w:sectPr>` through `</w:document>`)
3. Constructs new body content using the XML patterns above
4. Writes the combined result back to `document.xml`

Use `re.match(r'(.*?<w:body>\s*)', xml, re.DOTALL)` for the opening and `re.search(r'(<w:sectPr>.*?</w:sectPr>\s*</w:body>\s*</w:document>)', xml, re.DOTALL)` for the closing.

The table properties block (`<w:tblPr>` through `</w:tblGrid>`) should be copied verbatim from the template — never reconstruct it.

### Step 3: Add hyperlink relationships
If James's email isn't already in the rels file, add:
```xml
<Relationship Id="rId8" Type="http://schemas.openxmlformats.org/officeDocument/2006/relationships/hyperlink" Target="mailto:james@turingworks.ai" TargetMode="External"/>
```

### Step 4: Pack and validate
```bash
python scripts/office/pack.py /home/claude/dar_unpacked/ /home/claude/output.docx --original <skill_path>/assets/template.docx
python scripts/office/validate.py /home/claude/output.docx
```

### Step 5: Deliver
Copy to `/mnt/user-data/outputs/` with naming convention: `YYYYMMDD_[Client]_TW_Data_Access_Request.docx`

---

## GATHERING REQUIREMENTS

When Alasdair asks for a data access request, gather this information (ask if not provided):

1. **Client name** — for the title and filename
2. **Engagement description** — short name for the title (e.g. "AP Process Improvement")
3. **Target start date** — for the objective line
4. **Systems/tools needed** — what TW needs access to and at what level
5. **Google Workspace needs** — whether TW needs domain accounts, Drive access, email
6. **Collaboration tools** — Notion (accounts vs guest), Slack, other
7. **Key contact/owner** — who at the client should action the requests
8. **What's NOT needed** — explicitly exclude items (e.g. "no n8n", "no LLM keys", "no historical data")

If Alasdair provides most of this in a voice note or shorthand, fill in reasonable defaults and flag assumptions. The document is always marked "for discussion" — it's a starting point, not a contract.

---

## PRE-FLIGHT CHECKLIST

Before delivering:

- [ ] Landscape orientation preserved
- [ ] "Confidential | Turing Works" header present
- [ ] Title includes client name and engagement name
- [ ] Objective references correct start date
- [ ] Both email addresses hyperlinked
- [ ] Table column widths match template (14670 DXA total)
- [ ] Header row is dark grey (666666) with white text
- [ ] Section rows are light grey (f3f3f3) with bold text
- [ ] Every row has exactly 6 cells
- [ ] Owner column populated for each row
- [ ] File validates with no errors
- [ ] Filename follows convention: `YYYYMMDD_[Client]_TW_Data_Access_Request.docx`
