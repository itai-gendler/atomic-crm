---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Add task on a contact's page and enters a description, due date and type
  kind: actor
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts:
    - First name
    - Last name
  - entity: task
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::contact
- text: The Product creates the pending task for that contact, owned by the User, and marks the contact seen now
  kind: product
  actor: user
  entities:
  - entity: task
    effect: creates
    to: Pending
    facts:
    - Description
    - Type
    - Due date
    - Contact
    - Owner
  - entity: contact
    effect: changes
    facts:
    - Last seen
    - Pending tasks
  contexts:
    web:
      place: crm-web::workspace::contact
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/tasks/AddTask.tsx#AddTask
---

# Add a task to a contact

## Trigger

A User must get back to a contact.

## Outcome

The task is listed on the contact and on the User's dashboard.
