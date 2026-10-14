---
kind: primary
routes:
  web: Web
steps:
- text: The User selects contacts that all have a tag, chooses Tag and picks that tag
  kind: actor
  actor: user
  entities:
  - entity: tag
    effect: reads
    facts:
    - Name
    - Color
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::contacts
- text: Every selected contact already has the tag
  kind: condition
  entities:
  - entity: contact
    effect: reads
    facts:
    - Tags
  - entity: tag
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::contacts
- text: The Product takes the tag off every selected contact and reports how many lost it
  kind: product
  actor: user
  entities:
  - entity: contact
    effect: changes
    facts:
    - Tags
  - entity: tag
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::contacts
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/contacts/BulkTagButton.tsx#BulkTagButton
---

# Remove a tag from selected contacts

## Trigger

A User un-labels a group of contacts.

## Outcome

None of the selected contacts has the tag.
