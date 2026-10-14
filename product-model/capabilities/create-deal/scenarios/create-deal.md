---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses New Deal and enters its name, company, contacts, category, budget, expected closing date and stage
  kind: actor
  actor: user
  entities:
  - entity: company
    effect: reads
    facts: []
  - entity: contact
    effect: reads
    facts: []
  - entity: deal
    as: new-deal
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::new-deal
- text: The Product creates the active deal at the top of its stage, managed by the User, and moves the stage's other deals down one place
  kind: product
  actor: user
  entities:
  - entity: deal
    effect: creates
    as: new-deal
    to: Active
    facts:
    - Name
    - Description
    - Company
    - Contacts
    - Category
    - Budget
    - Expected closing date
    - Stage
    - Position
    - Account manager
    - Created at
  - entity: deal
    effect: changes
    as: other-deal
    facts:
    - Position
  contexts:
    web:
      place: crm-web::workspace::new-deal
- text: The Product returns to the board
  kind: product
  actor: user
  entities:
  - entity: deal
    effect: reads
    as: new-deal
    facts:
    - Name
    - Stage
  contexts:
    web:
      place: crm-web::workspace::deal-board
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/deals/DealCreate.tsx#DealCreate
- kind: code
  role: implementation
  target: src/components/atomic-crm/deals/DealInputs.tsx#DealInputs
---

# Create a deal

## Trigger

A sales opportunity appears.

## Outcome

The deal heads its stage's column.
