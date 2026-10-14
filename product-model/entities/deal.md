---
domain: deals
relations:
- entity: deal-note
  verb: has
  cardinality: one-to-many
- entity: contact
  verb: involves
  cardinality: many-to-many
references:
- kind: code
  role: implementation
  target: supabase/schemas/01_tables.sql
- kind: code
  role: implementation
  target: src/components/atomic-crm/deals/DealInputs.tsx
- kind: code
  role: implementation
  target: src/components/atomic-crm/types.ts
---

# Deal

A sales opportunity with a company, moved through the stages of the pipeline on the deal board until it is archived.

## Information kept

- **Name** — the deal name; required
- **Description** — free text about the deal
- **Company** — the company the deal is made with; required
- **Contacts** — the contacts involved in the deal
- **Category** — one of the configured deal categories
- **Budget** — the deal amount, in the configured currency
- **Expected closing date** — when the deal is expected to close
- **Stage** — the pipeline stage the deal is in
- **Position** — where the deal sits in its stage's column
- **Account manager** — the user who manages the deal
- **Archived on** — when the deal was archived
- **Created at** — when the deal was created
- **Last activity** — when the deal last changed

## States

### Active

The deal is on the board in its stage.

### Archived

The deal is off the board, listed with the archived deals.
