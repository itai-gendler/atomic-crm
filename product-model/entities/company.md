---
domain: companies
relations:
- entity: contact
  verb: employs
  cardinality: one-to-many
- entity: deal
  verb: has
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: supabase/schemas/01_tables.sql
- kind: code
  role: implementation
  target: supabase/schemas/03_views.sql
- kind: code
  role: implementation
  target: src/components/atomic-crm/companies/CompanyInputs.tsx
---

# Company

An organisation the team works with. Contacts work at a company and deals are made with one.

## Information kept

- **Name** — the company name; required
- **Logo** — the company logo, taken from its website when none is given
- **Sector** — one of the configured company sectors
- **Size** — the number of employees, as a size band
- **Website** — the company website
- **LinkedIn URL** — the company LinkedIn page
- **Phone number** — the company phone number
- **Address** — the street address
- **City** — the city
- **Zip code** — the postal code
- **State** — the state
- **Country** — the country
- **Description** — free text about the company
- **Context links** — links to pages about the company
- **Revenue** — the company revenue
- **Tax identifier** — the company tax identifier
- **Account manager** — the user who follows the company
- **Added on** — when the company was added
- **Number of contacts** — how many contacts work at the company
- **Number of deals** — how many deals are made with the company
