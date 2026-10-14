---
kind: edge
routes:
  web: Web
steps:
- text: The User opens Contacts
  kind: actor
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::contacts
- text: The CRM has no contact yet
  kind: condition
  entities:
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::contacts
- text: The Product offers to create a contact or import a CSV file
  kind: product
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::contacts
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/contacts/ContactEmpty.tsx#ContactEmpty
---

# An empty contact list offers to add or import

## Trigger

A User opens Contacts in a new CRM.

## Outcome

The User can start adding contacts.
