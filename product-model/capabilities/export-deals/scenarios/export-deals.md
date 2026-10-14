---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Export on the deal board
  kind: actor
  actor: user
  entities:
  - entity: deal
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::deal-board
- text: The Product downloads a CSV of the listed deals
  kind: product
  actor: user
  entities:
  - entity: deal
    effect: reads
    facts:
    - Name
    - Description
    - Company
    - Contacts
    - Category
    - Budget
    - Expected closing date
    - Stage
    - Account manager
    - Created at
  contexts:
    web:
      place: crm-web::workspace::deal-board
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/deals/DealList.tsx
---

# Export deals to CSV

## Trigger

A User reports on the pipeline outside the CRM.

## Outcome

The User has a deals CSV file.
