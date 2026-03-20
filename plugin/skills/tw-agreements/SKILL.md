---
name: tw-agreements
description: Generate Turing Works client engagement agreements as .docx files. Use this skill whenever Alasdair asks to create a client agreement, proposal letter, engagement letter, consulting contract, or SOW for a new client or project. Also trigger when the user says "agreement", "contract", "engagement letter", "SOW", "statement of work", "proposal letter", or references creating terms for a client engagement. This skill produces a branded, legally structured Word document following the established TW agreement template. Always use this skill even for quick drafts or when adapting an existing agreement for a new client.
---

# TW Client Agreement Generator

## Purpose

Generate Turing Works client engagement agreements as professional .docx files using the established template structure, formatting conventions, and standard legal clauses.

## When to use

- Creating a new client agreement from scratch
- Adapting the agreement template for a new client or project
- Regenerating an agreement with updated terms (e.g. different fee structure, scope changes)

## Prerequisites

Before generating, gather these **required variables** from the user. Ask for any that are missing:

| Variable | Example | Notes |
|---|---|---|
| `client_legal_name` | Lyka Pet Food Pty Ltd | Full legal entity name |
| `client_short_name` | Lyka | For informal references |
| `addressees` | Mr. Guedes, Ms. Tang, and Mr. Foong | Salutation names |
| `addressee_block` | Gabriel Guedes / COO & CFO / Lyka | Top-of-letter addressee |
| `project_name` | Improving AP Processes – Purchase-to-Pay Improvements | Bold project line |
| `project_description` | 1–2 paragraphs describing context and what TW will deliver | Section 1 content |
| `scope_intro` | One sentence describing the relationship being established | Opening of Section 2 |
| `scope_of_work` | Bullet structure describing what TW will do | Sub-section under Section 2 |
| `deliverables` | List of concrete outputs | Sub-section under Section 2 |
| `process_bullets` | How updates, access, and sign-off work | Sub-section under Section 2 |
| `fee_structure` | Fixed fee / hourly / retainer — amount, payment schedule | Sub-section under Section 2 |
| `systems_referenced` | Omni, NetSuite, Zudello, EFTsure | For ownership + process clauses |
| `term_description` | Phase-based / time-based / ongoing | Section 4 |
| `termination_terms` | Notice period, pro rata calculation method | Section 6 |
| `governing_law_state` | New South Wales / Victoria | Section 8 — defaults to NSW |

**Optional variables** (use defaults if not provided):

| Variable | Default |
|---|---|
| `tw_sender_name` | Alasdair Bell |
| `tw_sender_title` | Partner |
| `tw_sender_address` | 3/23-25 Christie Street, Wollstonecraft, Sydney, NSW 2065 |
| `currency` | AUD |
| `payment_terms_days` | 14 days |
| `confidentiality_survival_years` | 5 years |
| `non_compete_years` | 2 years |
| `promotion_rights_cobranded` | true (include co-branded case study line) |

---

## Document Structure

The agreement follows this exact section order. **Do not reorder, rename, or omit sections.**

1. **Description of the Project** — context + what TW will deliver
2. **Scope of Services** — with bold+underline sub-headers as L1 bullets:
   - **Scope of Work** — what will be done, deliverables listed here
   - **Process** — updates, system access, sign-off mechanism
   - **Fees & Invoicing** — fee structure, payment schedule, expense policy
   - **Ownership** — deliverables in client accounts, future work priced separately
   - **Promotion Rights** — anonymised wins + co-branded case study + no disclosure without approval
3. **Responsibilities** — TW skill/care, client feedback/access, internal champion, delay clause
4. **Term & Review** — duration or phase-based conclusion, extension mechanism
5. **Currency** — denomination, invoicing compliance
6. **Termination** — notice period, payment for completed work
7. **Confidentiality** — full clause (see template in `references/standard-clauses.md`)
8. **Governing Law** — state jurisdiction
9. **Intellectual Property** — full assignment + carve-outs for methods and case studies
10. **Non-Compete / Non-Solicitation** — lettered list (a, b, c)

Followed by a **signature block table** (two columns, no borders).

---

## Formatting Rules — CRITICAL

These formatting rules are non-negotiable. The agreement must match the established TW template exactly.

### Typography & Spacing
- **Font:** Arial, 11pt (22 half-points) throughout
- **Line spacing:** Single (240 twips). No exceptions.
- **Paragraph spacing:** `after: 0, before: 0` on every paragraph. Use blank `Paragraph` elements for visual separation between blocks.
- **Page size:** A4 (11906 × 16838 DXA)
- **Margins:** 1 inch all sides (1440 DXA)

### Section Headers
- **Bold inline text only.** Never use Word heading styles (HeadingLevel.HEADING_1 etc.).
- Format: `**1. Description of the Project**` as a bold paragraph, followed by a blank line, then body text.
- Sections 7, 8, 9, 10: bold title paragraph, then body text on the **next line** (no blank line between title and first body paragraph). Then blank line before next paragraph.

### Scope Sub-headers (Section 2)
- L1 bullets with **bold + underline** text: e.g. `Scope of Work`, `Process`, `Fees & Invoicing`, `Ownership`, `Promotion Rights`
- Content under each sub-header uses L2 bullets (dash style, indented)
- Deeper nesting (e.g. Part A / Part B work items) uses L1 bullets at indent level 2160 DXA

### Lists
- **L1 bullets:** bullet character `•`, indent left 720, hanging 360
- **L2 bullets:** dash character `–`, indent left 1440, hanging 360
- **Deep bullets:** bullet character `•`, indent left 2160, hanging 360
- **Lettered list (non-compete):** `a)`, `b)`, `c)` format, indent left 720, hanging 360
- Blank line between every bullet item

### Inline Formatting
- Bold for emphasis on key terms: `Receiving Party`, `Disclosing Party`, `Confidential Information`, `Effective Date`, fee amounts, payment term days
- Bold + italic for sub-part headings within scope (e.g. `Part A – KPI Definition...`)
- Italic for legislation references (e.g. `Privacy Act 1988 (Cth)`)
- Smart quotes throughout: use `\u201C` / `\u201D` for double quotes, `\u2018` / `\u2019` for single quotes and apostrophes
- En-dash `\u2013` for ranges and list separators

### Signature Block
- Borderless two-column table (width 9026 DXA, columns 4513 each)
- Left: "Signed for and on behalf of Turing Works"
- Right: "Signed for and on behalf of [Client Legal Name]"
- Fields: Name, Signature, Date with underscore lines

---

## Implementation

Use the `docx` npm package (`docx-js`). Read `/mnt/skills/public/docx/SKILL.md` for docx-js patterns and critical rules before generating.

A sanitized reference template is available at `assets/template.docx`. Use this to verify formatting, spacing, and structure — it shows the exact layout expected with all client-specific content replaced by `[PLACEHOLDER]` values.

### Key Implementation Notes

1. **All spacing via blank paragraphs.** Never use `spacing.after` or `spacing.before` on content paragraphs. Every paragraph gets `{ after: 0, before: 0, line: 240 }`.
2. **Numbering config:** Define separate references for `bullets1` (•), `bullets2` (–), and `letters` (a, b, c).
3. **Deep-indented bullets** don't use a separate numbering level — they reuse `bullets1` with an explicit `indent: { left: 2160, hanging: 360 }` override on the Paragraph.
4. **No border table** for signature block — use `BorderStyle.NONE` on all sides.
5. **Validate** with `python scripts/office/validate.py` after generation.
6. **Standard clauses** (Confidentiality, IP, Non-Compete) are in `references/standard-clauses.md`. Read that file and reproduce verbatim — do not paraphrase or shorten legal language.

---

## Process

1. Gather variables from user (ask for missing required ones)
2. Read `references/standard-clauses.md` for legal boilerplate
3. Read `/mnt/skills/public/docx/SKILL.md` for docx-js implementation patterns
4. Generate the .docx using docx-js
5. Validate with `validate.py`
6. Present to user via `present_files`
7. Iterate based on feedback
