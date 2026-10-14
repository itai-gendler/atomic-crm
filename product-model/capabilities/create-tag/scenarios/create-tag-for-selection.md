---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Tag on selected contacts, then Create new tag, and enters a name and colour
  kind: actor
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts: []
  - entity: tag
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::contacts
- text: The Product creates the tag and puts it on every selected contact
  kind: product
  actor: user
  entities:
  - entity: tag
    effect: creates
    facts:
    - Name
    - Color
  - entity: contact
    effect: changes
    facts:
    - Tags
  contexts:
    web:
      place: crm-web::workspace::contacts
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/contacts/BulkTagButton.tsx#BulkTagButton
---

# Create a tag for selected contacts

## Trigger

A group of contacts needs a new label.

## Outcome

The new tag exists on every selected contact.
