# Standard Clauses — Turing Works Client Agreements

These clauses are reproduced verbatim in every TW client agreement. Do not paraphrase, shorten, or restructure. Only the variables in `{braces}` change per engagement.

---

## Section 3: Responsibilities

Bullet list (L1 bullets, blank line between each):

- TW will perform services with reasonable skill and care
- Client will provide timely feedback and approvals and ensure access to required systems
- Client agrees to provision an internal employee for each project to assist with scope definition, sign-off, user feedback, or other necessary involvement.
- If feedback or approvals are delayed, project progress may be delayed accordingly, at the Client's expense

---

## Section 7: Confidentiality

**7. Confidentiality**
Both parties agree to keep confidential any non-public information shared during the engagement.

Each party (the **Receiving Party**) must keep confidential all information of the other party (the **Disclosing Party**) that is by its nature confidential, is designated as confidential, or that a reasonable person would consider confidential, including business strategies, financial data, customer information, trade secrets, technical information, pricing and proposals (**Confidential Information**).

**Exclusions.** Confidential Information does not include information that: (a) is or becomes public other than through breach; (b) was lawfully known to the Receiving Party before disclosure; (c) is independently developed without reference to the Disclosing Party's Confidential Information; or (d) is lawfully received from a third party without confidentiality obligations.

**Use & disclosure.** The Receiving Party may use Confidential Information solely to perform or receive the Services. It may disclose Confidential Information to its personnel, related bodies corporate, professional advisers and subcontractors who have a need to know and are bound by obligations no less protective.

**Compelled disclosure.** If legally required to disclose, the Receiving Party will (to the extent lawful) give prompt notice and reasonably cooperate to seek protective treatment.

**Care, return & survival.** The Receiving Party must protect Confidential Information using at least the same degree of care it uses for its own similar information (and no less than reasonable care). On request or termination, it will promptly return or destroy Confidential Information, except for legally required archival/back-up copies, which remain confidential. The obligations survive termination; for trade secrets, for so long as they remain trade secrets; for other Confidential Information, for **{confidentiality_survival_years}** after termination.

**Remedies.** The parties acknowledge damages may be inadequate and the Disclosing Party may seek injunctive or other equitable relief.

**Privacy.** To the extent Confidential Information includes personal information, each party will comply with applicable privacy laws (including the *Privacy Act 1988 (Cth)*).

---

## Section 8: Governing Law

**8. Governing Law**
This agreement is governed by the laws of {governing_law_state}, Australia.

---

## Section 9: Intellectual Property

**9. Intellectual Property**
TW agrees that all work product, deliverables, materials, inventions, discoveries, designs, developments, and other items of any kind created, prepared, or produced by TW in the course of performing services for Client (collectively, "Work Product") shall be the sole and exclusive property of Client. TW hereby assigns and agrees to assign to Client all right, title, and interest in and to such Work Product, including all associated intellectual property rights. TW agrees to execute any documents and take any actions reasonably requested by Client to evidence or perfect Client's ownership of the Work Product.

For clarity, this does not prevent TW from:

- Reusing its own underlying methods, frameworks, templates, or know-how developed during the course of providing services;
- Sharing anonymised case studies or generalised insights (that do not disclose Client's name, confidential information, or commercially sensitive details) for marketing and thought leadership purposes

---

## Section 10: Non-Compete / Non-Solicitation

**10. Non-Compete / Non-Solicitation**
During the term of this Agreement and for a period of {non_compete_years} following its termination, TW shall not, directly or indirectly:

a) engage in or provide services substantially similar to those provided to Client to any business that competes with Client;

b) solicit or attempt to solicit any of Client's customers, clients, or prospective customers with whom TW had contact during the term of this Agreement; or

c) recruit, solicit, or induce any employee, contractor, or representative of Client to terminate their relationship with Client

---

## Subcontracting (optional clause)

Include this as a standalone numbered clause (placed **after** Non-Compete, so existing sections do not renumber) whenever TW will use a subcontractor on the engagement. Informing the client is the trigger James requires; a client acknowledgement ("sounds good") is sufficient. Replace `{subcontractor_name}` with the named contractor, or omit that sentence to keep it generic.

**11. Subcontracting**
TW may engage subcontractors and other third-party personnel to perform any part of the Services. The Client acknowledges and approves that a significant portion of the work under this Agreement will be performed by {subcontractor_name}, an independent contractor engaged by TW, and that deliverables may be produced by that subcontractor.

TW remains responsible for the Services and for the acts and omissions of its subcontractors as if they were TW's own. TW will ensure that each subcontractor is bound by confidentiality and intellectual property obligations no less protective of the Client than those set out in this Agreement, so that all Work Product produced by a subcontractor vests in the Client in accordance with Section 9 (Intellectual Property).

The Client's approval of TW's subcontractors will not be unreasonably withheld. TW will notify the Client before engaging any additional subcontractor with material involvement in the Services.

Note: This clause is the head-agreement counterpart to the TW subcontractor agreement (see `subcontractor-clauses.md`). The two are designed to operate back-to-back.

---

## Promotion Rights (standard bullets)

These go under Section 2 > Promotion Rights sub-header:

- TW may reference anonymised "wins" from this work for marketing purposes with client approval, not to be unreasonably withheld
- TW and Client will collaborate on a co-branded case study to be published on LinkedIn and featured on TW's website, with final copy subject to Client approval prior to publication
- No Client name or commercially sensitive information will be disclosed without Client's prior written approval

Note: The co-branded case study line is included by default. Set `promotion_rights_cobranded: false` to omit it.

---

## Sender Block (default)

```
{tw_sender_name}
{tw_sender_title}
{tw_sender_address_line1}
{tw_sender_address_line2}
{tw_sender_address_line3}
```

Defaults:
```
Alasdair Bell
Partner
3/23-25 Christie Street
Wollstonecraft
Sydney, NSW 2065
```

---

## Salutation Format

`Dear {addressees},`

Bold, on its own line. Followed by blank line, then opening paragraph.

## Opening Paragraph (template)

Further to our recent conversations, we, Turing Works ("we" or "TW"), look forward to working with you and your team on the {project_name_underlined} project. For the purpose of this agreement and its terms, this agreement is between Turing Works ("TW") and {client_legal_name} ("Client").

In this Proposal Letter, we outline the Services, Deliverables and Products that we will be providing to you, as well as the terms and conditions that govern this engagement.

Note: `{project_name_underlined}` should be rendered with underline formatting in the .docx.
