---
kind: primary
routes:
  web: Web
steps:
- text: The User selects contacts in the list, chooses Tag and picks a tag
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
- text: The Product adds the tag to each selected contact that lacks it and reports how many were tagged
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
      place: crm-web::workspace::contacts
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/contacts/BulkTagButton.tsx#BulkTagButton
- kind: code
  role: implementation
  target: e2e/bulkContactTags.spec.ts
---

# Tag selected contacts

## Trigger

A User labels a group of contacts.

## Outcome

Every selected contact has the tag.
