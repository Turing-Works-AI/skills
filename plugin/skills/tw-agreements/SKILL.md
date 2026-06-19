---
name: tw-agreements
description: Generate Turing Works agreements as .docx files — both client engagement agreements and subcontractor agreements. Use this skill whenever Alasdair asks to create a client agreement, proposal letter, engagement letter, consulting contract, SOW, or a subcontractor / consultant agreement for someone delivering work on a TW project. Also trigger when the user says "agreement", "contract", "engagement letter", "SOW", "statement of work", "proposal letter", "subcontractor agreement", "consultant agreement", or references creating terms for a client engagement or for a contractor delivering work for TW. This skill produces a branded, legally structured Word document following the established TW agreement templates. Always use this skill even for quick drafts or when adapting an existing agreement for a new client or subcontractor.
---

# TW Agreement Generator

## Purpose

Generate Turing Works agreements as professional .docx files using the established template structure, formatting conventions, and standard legal clauses. The skill has two branches: **Client Engagement Agreements** and **Subcontractor Agreements**.

## Agreement types — pick the branch first

| Branch | Use when | Parties | Clauses file | Template asset |
|---|---|---|---|---|
| **Client Engagement** | TW is contracting with a client to deliver a project | Turing Works ↔ Client | `references/standard-clauses.md` | `assets/template.docx` |
| **Subcontractor** | A contractor/consultant is delivering work *for TW* on a TW project | Turing Works ↔ Subcontractor's entity | `references/subcontractor-clauses.md` | `assets/subcontractor-template.docx` |

The two are designed to operate **back-to-back**: when TW uses a subcontractor, the client agreement should carry the optional **Subcontracting** clause (`standard-clauses.md`), and the subcontractor agreement's liability sits at or above TW's exposure to the client. See "Subcontractor Agreement branch" below.

The **Formatting Rules** and **Implementation** sections are shared by both branches. Everything from "Document Structure" down marked "(Client branch)" is client-specific; the subcontractor branch has its own structure and variables.

## When to use

- Creating a new client agreement from scratch
- Adapting the agreement template for a new client or project
- Regenerating an agreement with updated terms (e.g. different fee structure, scope changes)
- Drafting a subcontractor / consultant agreement for someone delivering work on a TW engagement

## Prerequisites (Client branch)

Before generating a **client agreement**, gather these **required variables** from the user. Ask for any that are missing:

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

## Document Structure (Client branch)

The client agreement follows this exact section order. **Do not reorder, rename, or omit sections.**

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

**Optional — Subcontracting (Section 11).** When TW will use a subcontractor on the engagement, add the **Subcontracting** clause from `references/standard-clauses.md` as a standalone Section 11 (placed after Non-Compete so nothing renumbers). This is the head-agreement counterpart that makes the subcontractor arrangement back-to-back. James's rule: build it in and inform the client; the client's acknowledgement ("sounds good") is sufficient.

---

## Subcontractor Agreement branch

Use this branch when a contractor/consultant is delivering work **for TW** on a TW project. The agreement is between **TW and the subcontractor's own legal entity** — never between the subcontractor and TW's end client. Clauses are in `references/subcontractor-clauses.md` (read and reproduce verbatim); the sanitized layout reference is `assets/subcontractor-template.docx`.

### Core framing (James's rules — do not get these wrong)

- Frame the subcontractor in the recitals as **a consultant to TW, engaged for a defined period to assist on a specific project**.
- The subcontractor is engaged by TW only, with **no contractual relationship with, or claim against, TW's client**.
- The subcontractor does **not** review the client (head) agreement; they review and sign only their own.
- **Liability is back-to-back**: the subcontractor's liability sits **at or above** TW's exposure to the client under the head agreement. Never cap it below — otherwise TW stays liable upstream but cannot recover downstream.
- **Do not proactively include a liability cap in the subcontractor's favour.** Only add one if they ask, capped to project value, and only if it stays at/above TW's upstream exposure (fallback wording is in `subcontractor-clauses.md`).
- **Insurance is mandatory**: the subcontractor holds their own professional indemnity + public liability cover and provides certificates of currency on request.
- **Fee is deliverable / milestone-based** ("this much work for this much money"); default split 50:50 (commencement / completion-and-acceptance). When deliverables are known, write the specific line items into the contract.
- **Start date** aligns with the head engagement, with flexibility built in.

### Required variables

Gather these (ask for any missing). Deliverables/scope and fee may be deferred to a scoping discussion — use highlighted placeholders in the draft if so.

| Variable | Example | Notes |
|---|---|---|
| `subcontractor_entity` | Joanne Kim Consulting Pty Ltd | Subcontractor's **legal entity** name — the party + signature block |
| `subcontractor_first_name` | Joanne | Salutation |
| `project_name` | Consultant engagement — support on TW client delivery | Bold project line (kept generic; no need to expose client terms) |
| `scope_of_work` | Defined scope, or `[placeholder]` if deferred | Section 2 › Scope of Work |
| `deliverables` | Milestone line items, or `[placeholder]` if deferred | Section 2 › Deliverables |
| `total_fee` + `instalment` | $X,XXX + GST, 50/50 split | Section 2 › Fees & Invoicing |
| `start_date` | Aligned to head engagement, or `[placeholder]` | Section 4 |
| `governing_law_state` | New South Wales | Section 10 — defaults to NSW |

Optional variables (`currency`, `payment_terms_days`, `termination_notice`, `confidentiality_survival_years`, `tw_sender_*`) share the Client-branch defaults.

### Document structure (Subcontractor branch)

**Do not reorder, rename, or omit sections.** Sub-headers under Section 2 use the same bold+underline L1-bullet convention as the client branch.

1. **Background** — consultant-to-TW framing; Head Engagement; back-to-back intent
2. **Scope of Services** — sub-headers: **Scope of Work** · **Deliverables** · **Conditions of Work** (independent-contractor terms) · **Fees & Invoicing** (50:50 milestone) · **Ownership**
3. **Responsibilities**
4. **Term & Start Date** — aligned to head engagement, flexibility built in
5. **Currency**
6. **Termination** — 14-day notice + immediate for breach/insurance failure + flow-through if Head Engagement ends
7. **Confidentiality** — shared clause from `standard-clauses.md` + line covering the client's Confidential Information
8. **Insurance** — own PI + public liability, certificates on request
9. **Liability** — back-to-back, flow-through indemnity, not capped below TW's upstream exposure
10. **Governing Law**
11. **Intellectual Property** — Work Product assigns to TW (so TW can satisfy the client); carve-out for the subcontractor's own methods/know-how

Followed by a **signature block table** (Turing Works / subcontractor entity).

Placeholders for deferred content (entity, fee, start date, deliverables) should be **highlighted** in the draft so they are easy to spot — use run shading `{ type: ShadingType.CLEAR, fill: "FFFF00" }` (not the `highlight` property, which emits invalid XML).

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

A sanitized reference template is available for each branch — `assets/template.docx` (Client) and `assets/subcontractor-template.docx` (Subcontractor). Use the one matching your branch to verify formatting, spacing, and structure — it shows the exact layout expected with client/subcontractor-specific content replaced by `[PLACEHOLDER]` values.

### Key Implementation Notes

1. **All spacing via blank paragraphs.** Never use `spacing.after` or `spacing.before` on content paragraphs. Every paragraph gets `{ after: 0, before: 0, line: 240 }`.
2. **Numbering config:** Define separate references for `bullets1` (•), `bullets2` (–), and `letters` (a, b, c).
3. **Deep-indented bullets** don't use a separate numbering level — they reuse `bullets1` with an explicit `indent: { left: 2160, hanging: 360 }` override on the Paragraph.
4. **No border table** for signature block — use `BorderStyle.NONE` on all sides.
5. **Validate** with `python scripts/office/validate.py` after generation.
6. **Standard clauses** are in `references/standard-clauses.md` (Client branch: Confidentiality, IP, Non-Compete, optional Subcontracting) and `references/subcontractor-clauses.md` (Subcontractor branch: Background, Conditions of Work, Insurance, Liability, IP). Read the file for your branch and reproduce verbatim — do not paraphrase or shorten legal language.
7. **Highlighted placeholders.** For deferred content, use bold + run shading `{ type: ShadingType.CLEAR, fill: "FFFF00" }` so the user can spot fill-ins. Do not use the `highlight` property — it emits an invalid `highlightCs` element.

---

## Process

1. **Pick the branch** — Client Engagement or Subcontractor (see "Agreement types")
2. Gather variables from user (ask for missing required ones; placeholders are fine for deferred scope/fee)
3. Read the clauses file for your branch (`standard-clauses.md` and/or `subcontractor-clauses.md`) for legal boilerplate
4. Read the docx skill for docx-js implementation patterns
5. Generate the .docx using docx-js
6. Validate with `validate.py`
7. Present to user
8. Iterate based on feedback
