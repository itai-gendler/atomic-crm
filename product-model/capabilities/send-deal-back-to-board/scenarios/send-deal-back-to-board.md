---
kind: primary
routes:
  web: Web
steps:
- text: The User opens an archived deal and chooses Send back to the board
  kind: actor
  actor: user
  entities:
  - entity: deal
    effect: reads
    as: returned-deal
    facts:
    - Name
    - Archived on
  contexts:
    web:
      place: crm-web::workspace::deal
- text: The Product puts the deal back at the top of its stage, shifts that stage's deals down and returns to the board
  kind: product
  actor: user
  entities:
  - entity: deal
    effect: changes
    as: returned-deal
    from: Archived
    to: Active
    facts:
    - Archived on
    - Position
  - entity: deal
    effect: changes
    as: other-deal
    facts:
    - Position
  contexts:
    web:
      place: crm-web::workspace::deal
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/deals/DealShow.tsx#DealShow
- kind: code
  role: implementation
  target: src/components/atomic-crm/providers/supabase/dataProvider.ts
---

# Send a deal back to the board

## Trigger

An archived deal comes back to life.

## Outcome

The deal heads its stage's column again.
