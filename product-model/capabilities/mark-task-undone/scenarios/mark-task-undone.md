---
kind: primary
routes:
  web: Web
steps:
- text: The User unchecks a task that was done
  kind: actor
  actor: user
  entities:
  - entity: task
    effect: reads
    facts:
    - Description
    - Done date
  contexts:
    web:
      place: crm-web::workspace::dashboard
- text: The Product clears the task's done date
  kind: product
  actor: user
  entities:
  - entity: task
    effect: changes
    from: Done
    to: Pending
    facts:
    - Done date
  contexts:
    web:
      place: crm-web::workspace::dashboard
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/tasks/Task.tsx#Task
---

# Untick a task

## Trigger

A task was ticked off by mistake.

## Outcome

The task is pending again.
