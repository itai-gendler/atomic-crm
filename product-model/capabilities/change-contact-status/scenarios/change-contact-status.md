---
kind: primary
routes:
  web: Web
steps:
- text: The User picks a status in the contact's Status section
  kind: actor
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts:
    - Status
  contexts:
    web:
      place: crm-web::workspace::contact
- text: The Product saves the contact's new status
  kind: product
  actor: user
  entities:
  - entity: contact
    effect: changes
    facts:
    - Status
  contexts:
    web:
      place: crm-web::workspace::contact
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/contacts/ContactInputs.tsx#ContactStatusSelector
---

# Change a contact's status

## Trigger

A contact becomes hotter or colder.

## Outcome

The contact carries the new status in lists and on the dashboard.
