---
name: invoice-maker
description: Generate branded Turing Works invoices as Word documents (.docx). Use this skill whenever Alasdair asks to create an invoice, bill a client, send a bill, generate billing documentation, or produce an invoice for client work. Also trigger when he mentions "invoice", "bill them for", "send an invoice", "billing", "create a bill", or references payment documentation. This skill handles formatting, GST calculations, QR code generation, and outputs a branded .docx matching the TW invoice template. Even for quick "just make me an invoice" requests, use this skill.
---

# Invoice Maker

Generate professional Turing Works invoices as .docx files. The script uses the branded template (teal header, line item table, bank details, Wise QR code) and handles all GST calculations automatically.

## What You Need From the User

Gather these before generating. If the user gives a rough description of the work, wordsmith it into professional invoice language (see guidelines below).

| Field | Format | Example |
|---|---|---|
| **Invoice code** | 3-letter client code + 4-digit sequential number | `LYK0001` |
| **Client name** | Full company/entity name | `Lyka Pet Food Pty Ltd` |
| **Client address** | List of lines: street, suburb, state, postcode | `["Level 1, 123 Example St", "Sydney", "NSW", "2000"]` |
| **Line items** | Each: short name, description, amount inc GST | See below |
| **Payment link** | Wise payment URL | `https://wise.com/pay/r/xxx` |
| **Bank reference** | Reference for bank transfer | `139904` |

**Optional** (have sensible defaults):

| Field | Default |
|---|---|
| Invoice date | Today |
| Payment terms | 14 days (added to invoice date for due date) |

## Wordsmithing Line Item Descriptions

The user will give a rough description. Turn it into clean, specific invoice language:

- "June AI work for Lyka" becomes "AI Analytics and Automation Consulting - June 2026"
- "workshop and initial setup" becomes "AI Operations Workshop and Implementation Setup"
- "monthly retainer March" becomes "Monthly Retainer - AI Automation Services - March 2026"
- "data pipeline build" becomes "Data Pipeline Development and Integration"

Keep descriptions concise but specific. Include the time period where applicable. Use title case.

For the **item** field (short name), use a 2-4 word category like "Engagement Fee", "Workshop Fee", "Monthly Retainer", "Project Milestone".

## How to Generate

### Step 1: Create a JSON config file

```json
{
  "invoice_code": "LYK0003",
  "client_name": "Lyka Pet Food Pty Ltd",
  "client_address": ["Level 1, 123 Example St", "Sydney", "NSW", "2000"],
  "invoice_date": "2026-03-28",
  "bank_reference": "139904",
  "payment_link": "https://wise.com/pay/r/h_example",
  "line_items": [
    {
      "item": "Monthly Retainer",
      "description": "AI Analytics and Automation Consulting - March 2026",
      "amount_inc_gst": 5500.00
    }
  ]
}
```

For **multiple line items**, add more objects to the array:

```json
"line_items": [
  {
    "item": "Workshop Fee",
    "description": "AI Operations Workshop - Half Day",
    "amount_inc_gst": 2750.00
  },
  {
    "item": "Implementation Fee",
    "description": "Automation Implementation and Configuration - March 2026",
    "amount_inc_gst": 5500.00
  }
]
```

### Step 2: Run the generator

Save the config as a temp JSON file, then run:

```bash
python3 <skill-dir>/scripts/generate_invoice.py /tmp/invoice_config.json <output_path.docx>
```

If no output path is given, it defaults to `YYYYMMDD_Invoice_{CODE}.docx` in the current directory.

The script requires `python-docx`, `qrcode`, and `Pillow` — it auto-installs them if missing.

### Step 3: Confirm with the user

Tell the user the invoice has been generated and where the file is. Mention the key details so they can verify: client name, invoice code, total amount (inc GST), and due date.

## What the Script Does Automatically

- Calculates GST at 10% (amount ex-GST = amount inc-GST / 1.10)
- Sets due date to invoice date + 14 days
- Generates a QR code from the Wise payment link
- Populates all fixed company details (Turing Works, ABN, address, bank account)
- Handles any number of line items (adds rows to the table as needed)
- Outputs a branded .docx matching the TW invoice template

## Fixed Details (baked into the template and script)

- **Entity:** Turing Works - General Partnership
- **ABN:** 78 723 794 381
- **Address:** 16 Forbes street, Rye, Victoria, Australia, 3941
- **Bank:** Account Name: Turing Works, BSB: 774001, Acc/No: 231410692
- **GST:** 10% (Australian standard)
- **Payment terms:** 14 days

## File Structure

```
Invoice-maker/
├── SKILL.md              ← you are here
├── scripts/
│   └── generate_invoice.py   ← the generator script
├── assets/
│   ├── template.docx     ← branded invoice template
│   └── tw_logo.png       ← TW logo (white, for teal header)
└── evals/
    └── evals.json        ← test cases
```
