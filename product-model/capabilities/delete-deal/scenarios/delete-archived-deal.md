---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Delete on an archived deal
  kind: actor
  actor: user
  entities:
  - entity: deal
    effect: reads
    facts:
    - Name
    - Archived on
  contexts:
    web:
      place: crm-web::workspace::deal
- text: The Product removes the deal and its notes
  kind: product
  actor: user
  entities:
  - entity: deal
    effect: removes
    from: Archived
  - entity: deal-note
    effect: removes
    with: deal
  contexts:
    web:
      place: crm-web::workspace::deal
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/deals/DealShow.tsx#DealShow
---

# Delete an archived deal

## Trigger

An archived deal is no longer worth keeping.

## Outcome

The deal is gone.
