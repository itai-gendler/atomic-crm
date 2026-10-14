---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Delete while editing a deal
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
- text: The Product removes the deal and its notes, offering Undo for a few seconds
  kind: product
  actor: user
  entities:
  - entity: deal
    effect: removes
    from: Active
  - entity: deal-note
    effect: removes
    with: deal
  contexts:
    web:
      place: crm-web::workspace::deal
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/deals/DealEdit.tsx#DealEdit
---

# Delete a deal being edited

## Trigger

A deal was entered by mistake.

## Outcome

The deal and its notes are gone.
