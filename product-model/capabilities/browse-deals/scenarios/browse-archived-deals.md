---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses View archived deals under the board
  kind: actor
  actor: user
  entities:
  - entity: deal
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::deal-board
- text: The Product lists archived deals grouped by the day they were archived, most recent first
  kind: product
  actor: user
  entities:
  - entity: deal
    effect: reads
    facts:
    - Name
    - Company
    - Budget
    - Category
    - Archived on
  contexts:
    web:
      place: crm-web::workspace::deal-board
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/deals/DealArchivedList.tsx#DealArchivedList
---

# Look up archived deals

## Trigger

A User looks for a deal taken off the board.

## Outcome

The User sees the archived deals.
