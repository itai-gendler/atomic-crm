---
kind: primary
routes:
  web: Web
steps:
- text: The User removes a tag chip from a contact
  kind: actor
  actor: user
  entities:
  - entity: tag
    effect: reads
    facts:
    - Name
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::contact
- text: The Product takes the tag off the contact
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
      place: crm-web::workspace::contact
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/contacts/TagsListEdit.tsx#TagsListEdit
---

# Remove a tag from a contact

## Trigger

A label no longer applies.

## Outcome

The contact no longer shows the tag.
