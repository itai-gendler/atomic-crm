---
kind: validation
routes:
  web: Web
steps:
- text: The User saves a deal without its name, company, budget, expected closing date or stage
  kind: actor
  actor: user
  entities:
  - entity: company
    effect: reads
    facts: []
  - entity: deal
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::new-deal
- text: The Product marks the missing fields as required and creates nothing
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace::new-deal
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/deals/DealInputs.tsx#DealInputs
---

# A deal needs a name, company, budget, closing date and stage

## Trigger

A User leaves a required field empty.

## Outcome

No deal is created.
