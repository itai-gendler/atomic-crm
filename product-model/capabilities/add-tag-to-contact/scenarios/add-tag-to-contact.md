---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Add tag on a contact and picks a tag it does not have
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
      place: crm-web::workspace::contact
- text: The Product adds the tag to the contact
  kind: product
  actor: user
  entities:
  - entity: contact
    effect: changes
    facts:
    - Tags
  - entity: tag
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: crm-web::workspace::contact
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/contacts/TagsListEdit.tsx#TagsListEdit
---

# Tag a contact

## Trigger

A User labels a contact.

## Outcome

The contact shows the tag.
