---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Create new tag on a contact and enters a name and colour
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
      place: crm-web::workspace::contact
- text: The Product creates the tag and puts it on the contact
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
      place: crm-web::workspace::contact
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/tags/TagCreateModal.tsx
- kind: code
  role: implementation
  target: src/components/atomic-crm/tags/useCreateTag.ts
---

# Create a tag on a contact

## Trigger

No existing tag fits.

## Outcome

The new tag exists and the contact has it.
