---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Edit in a task's menu and changes it
  kind: actor
  actor: user
  entities:
  - entity: task
    effect: reads
    facts:
    - Description
    - Type
    - Due date
  contexts:
    web:
      place: crm-web::workspace::dashboard
- text: The Product saves the task
  kind: product
  actor: user
  entities:
  - entity: task
    effect: changes
    facts:
    - Description
    - Type
    - Due date
  contexts:
    web:
      place: crm-web::workspace::dashboard
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/tasks/TaskEdit.tsx
- kind: code
  role: implementation
  target: src/components/atomic-crm/tasks/Task.tsx#Task
---

# Edit a task

## Trigger

A task's details change.

## Outcome

The task shows the new details.
