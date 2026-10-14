---
kind: primary
routes:
  web: Web
steps:
- text: The User drags a deal up or down its column
  kind: actor
  actor: user
  entities:
  - entity: deal
    effect: reads
    as: moved-deal
    facts:
    - Name
    - Position
  contexts:
    web:
      place: crm-web::workspace::deal-board
- text: The Product moves the deal to the dropped place and shifts the deals between
  kind: product
  actor: user
  entities:
  - entity: deal
    effect: changes
    as: moved-deal
    facts:
    - Position
  - entity: deal
    effect: changes
    as: other-deal
    facts:
    - Position
  contexts:
    web:
      place: crm-web::workspace::deal-board
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/deals/DealListContent.tsx#DealListContent
---

# Reorder a deal within its stage

## Trigger

A User prioritises deals within a stage.

## Outcome

The column shows the new order.
