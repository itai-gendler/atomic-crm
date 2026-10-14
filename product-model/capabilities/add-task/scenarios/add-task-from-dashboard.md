---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Create task on the dashboard, picks a contact and enters a description, due date and type
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
      place: crm-web::workspace::dashboard
- text: The Product creates the pending task, owned by the User, and marks the contact seen now
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
      place: crm-web::workspace::dashboard
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/tasks/AddTask.tsx#AddTask
- kind: code
  role: implementation
  target: e2e/userAddingATask.spec.ts
---

# Add a task from the dashboard

## Trigger

A User plans a follow-up from the task list.

## Outcome

The task appears in the User's upcoming tasks.
