---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Delete on a contact's page
  kind: actor
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::contact
- text: The Product removes the contact with its notes and tasks and returns to the list, offering Undo for a few seconds
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
      place: crm-web::workspace::contact
references:
- kind: code
  role: implementation
  target: src/components/admin/delete-button.tsx#DeleteButton
- kind: code
  role: implementation
  target: supabase/schemas/01_tables.sql
---

# Delete a contact

## Trigger

A contact is no longer relevant.

## Outcome

The contact, its notes and its tasks are gone.
