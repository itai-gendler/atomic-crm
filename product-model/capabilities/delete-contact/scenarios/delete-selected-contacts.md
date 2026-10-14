---
kind: primary
routes:
  web: Web
steps:
- text: The User selects contacts in the list and chooses Delete
  kind: actor
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::contacts
- text: The Product removes every selected contact with its notes and tasks
  kind: product
  actor: user
  entities:
  - entity: contact
    effect: removes
  - entity: contact-note
    effect: removes
    with: contact
  - entity: task
    effect: removes
    as: pending-task
    from: Pending
    with: contact
  - entity: task
    effect: removes
    as: done-task
    from: Done
    with: contact
  contexts:
    web:
      place: crm-web::workspace::contacts
references:
- kind: code
  role: implementation
  target: src/components/admin/bulk-delete-button.tsx
- kind: code
  role: implementation
  target: src/components/atomic-crm/contacts/ContactList.tsx#ContactList
---

# Delete selected contacts

## Trigger

A User cleans up several contacts at once.

## Outcome

The selected contacts are gone.
