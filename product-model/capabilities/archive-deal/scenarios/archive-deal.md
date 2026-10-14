---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Archive on an active deal
  kind: actor
  actor: user
  entities:
  - entity: deal
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: crm-web::workspace::deal
- text: The Product archives the deal now, confirms Deal archived and returns to the board
  kind: product
  actor: user
  entities:
  - entity: deal
    effect: changes
    from: Active
    to: Archived
    facts:
    - Archived on
  contexts:
    web:
      place: crm-web::workspace::deal
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/deals/DealShow.tsx#DealShow
---

# Archive a deal

## Trigger

A deal is closed or abandoned.

## Outcome

The deal is off the board and among the archived deals.
