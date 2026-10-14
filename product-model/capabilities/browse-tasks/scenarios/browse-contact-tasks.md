---
kind: primary
routes:
  web: Web
steps:
- text: The User opens a contact's page
  kind: actor
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts:
    - First name
    - Last name
  contexts:
    web:
      place: crm-web::workspace::contact
- text: The Product lists the contact's tasks by due date
  kind: product
  actor: user
  entities:
  - entity: task
    effect: reads
    facts:
    - Description
    - Type
    - Due date
    - Done date
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::contact
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/contacts/ContactAside.tsx#ContactAside
- kind: code
  role: implementation
  target: src/components/atomic-crm/contacts/ContactTasksList.tsx
---

# See a contact's tasks

## Trigger

A User prepares a call with a contact.

## Outcome

The User sees every task about the contact.
