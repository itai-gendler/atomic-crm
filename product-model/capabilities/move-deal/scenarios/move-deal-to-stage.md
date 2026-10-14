---
kind: primary
routes:
  web: Web
steps:
- text: The User drags a deal into another stage's column
  kind: actor
  actor: user
  entities:
  - entity: deal
    effect: reads
    as: moved-deal
    facts:
    - Name
    - Stage
  contexts:
    web:
      place: crm-web::workspace::deal-board
- text: The Product puts the deal in that stage at the dropped place and renumbers both columns, unfiltered deals included
  kind: product
  actor: user
  entities:
  - entity: deal
    effect: changes
    as: moved-deal
    facts:
    - Stage
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

# Move a deal to another stage

## Trigger

A deal progresses, stalls or closes.

## Outcome

The deal sits in its new stage.
