---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Edit on a deal and changes its details
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
- text: The Product saves the deal, confirms Deal updated and shows the deal again
  kind: product
  actor: user
  entities:
  - entity: deal
    effect: changes
    facts:
    - Name
    - Description
    - Company
    - Contacts
    - Category
    - Budget
    - Expected closing date
    - Stage
  contexts:
    web:
      place: crm-web::workspace::deal
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/deals/DealEdit.tsx#DealEdit
---

# Edit a deal

## Trigger

A deal's terms change.

## Outcome

The deal shows the new details.
