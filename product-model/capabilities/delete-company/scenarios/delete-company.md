---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Delete on a company's page
  kind: actor
  actor: user
  entities:
  - entity: company
    effect: reads
    facts:
    - Name
    - Number of contacts
    - Number of deals
  contexts:
    web:
      place: crm-web::workspace::company
- text: The Product removes the company, its contacts with their notes and tasks, and its deals with their notes, offering Undo for a few seconds
  kind: product
  actor: user
  entities:
  - entity: company
    effect: removes
  - entity: contact
    effect: removes
    with: company
  - entity: contact-note
    effect: removes
    with: contact
  - entity: task
    effect: removes
    as: pending-task
    from: Pending
    with: contact
  - entity: task
    effect: removes
    as: done-task
    from: Done
    with: contact
  - entity: deal
    effect: removes
    from: Active
    with: company
  - entity: deal-note
    effect: removes
    with: deal
  contexts:
    web:
      place: crm-web::workspace::company
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/companies/CompanyAside.tsx#CompanyAside
- kind: code
  role: implementation
  target: supabase/schemas/01_tables.sql
---

# Delete a company

## Trigger

An organisation is no longer relevant to the team.

## Outcome

The company and everything attached to it are gone.
