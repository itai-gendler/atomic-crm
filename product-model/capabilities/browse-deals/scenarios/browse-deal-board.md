---
kind: primary
routes:
  web: Web
steps:
- text: The User opens Deals
  kind: actor
  actor: user
  entities:
  - entity: deal
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::deal-board
- text: The Product shows the active deals in a column per stage, in their order, each column with its total budget
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
    - Stage
    - Position
  - entity: configuration
    effect: reads
    facts:
    - Deal stages
    - Currency
  contexts:
    web:
      place: crm-web::workspace::deal-board
- text: The User searches and filters by company, category, or Only deals I manage
  kind: actor
  actor: user
  entities:
  - entity: deal
    effect: reads
    facts:
    - Company
    - Category
    - Account manager
  - entity: company
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::deal-board
- text: The Product keeps only the matching deals on the board
  kind: product
  actor: user
  entities:
  - entity: deal
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: crm-web::workspace::deal-board
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/deals/DealList.tsx
- kind: code
  role: implementation
  target: src/components/atomic-crm/deals/DealListContent.tsx#DealListContent
- kind: code
  role: implementation
  target: src/components/atomic-crm/deals/DealColumn.tsx
---

# Browse the deal board

## Trigger

A User reviews the pipeline.

## Outcome

The User sees where each deal stands.

## Edge cases

- An Admin filters by any user as account manager instead of Only deals I manage.
