---
kind: primary
routes:
  web: Web
steps:
- text: The User opens a company's Activity tab
  kind: actor
  actor: user
  entities:
  - entity: company
    effect: reads
    facts:
    - Name
  - entity: activity
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::company
- text: The Product lists what was added about the company and its contacts and deals, newest first
  kind: product
  actor: user
  entities:
  - entity: activity
    effect: reads
    facts:
    - Event
    - Date
    - Added by
    - Record
  - entity: company
    effect: reads
    facts: []
  - entity: contact
    effect: reads
    facts: []
  - entity: deal
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::company
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/companies/CompanyShow.tsx#CompanyShow
- kind: code
  role: implementation
  target: supabase/schemas/03_views.sql
---

# See a company's activity

## Trigger

A User prepares a meeting with a company.

## Outcome

The User sees the history of the account.
