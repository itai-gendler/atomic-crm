---
kind: validation
routes:
  web: Web
steps:
- text: The User saves a new contact without a first or last name
  kind: actor
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::new-contact
- text: The Product marks the name as required and creates nothing
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace::new-contact
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/contacts/ContactInputs.tsx#ContactInputs
---

# A contact needs a first and last name

## Trigger

A User forgets the name.

## Outcome

No contact is created.
