---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Delete in a task's menu
  kind: actor
  actor: user
  entities:
  - entity: task
    effect: reads
    facts:
    - Description
  contexts:
    web:
      place: crm-web::workspace::dashboard
- text: The Product removes the task, offering Undo for a few seconds
  kind: product
  actor: user
  entities:
  - entity: task
    effect: removes
    from: Pending
  contexts:
    web:
      place: crm-web::workspace::dashboard
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/tasks/Task.tsx#Task
---

# Delete a task

## Trigger

A task is no longer needed.

## Outcome

The task is gone.
