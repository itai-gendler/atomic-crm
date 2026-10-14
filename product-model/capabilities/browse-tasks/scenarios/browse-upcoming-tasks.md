---
kind: primary
routes:
  web: Web
steps:
- text: The User opens the dashboard
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: crm-web::workspace::dashboard
- text: The Product lists the User's pending tasks grouped as Overdue, Today, Tomorrow, This week and Later, each with its contact
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
    - Contact
    - Owner
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::dashboard
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/tasks/TasksListByDueDate.tsx
- kind: code
  role: implementation
  target: src/components/atomic-crm/tasks/tasksPredicate.ts
---

# See one's upcoming tasks

## Trigger

A User plans their day.

## Outcome

The User sees what is due and when.

## Edge cases

- Tasks done in the last few minutes stay listed, struck through.
- Each group shows a few tasks and loads more on demand.
