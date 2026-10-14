---
kind: edge
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
- text: The CRM has neither deals nor contacts
  kind: condition
  entities:
  - entity: deal
    effect: reads
    facts: []
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::deal-board
- text: The Product asks the User to add a first contact before creating a deal
  kind: product
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts: []
  - entity: deal
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::deal-board
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/deals/DealEmpty.tsx#DealEmpty
---

# Deals start once a contact exists

## Trigger

A User opens Deals in an empty CRM.

## Outcome

The User is pointed to adding a contact first.
