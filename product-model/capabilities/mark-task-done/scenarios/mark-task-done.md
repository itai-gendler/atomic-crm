---
kind: primary
routes:
  web: Web
steps:
- text: The User checks a pending task
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
- text: The Product marks the task done now and keeps it struck through in the list for a few minutes
  kind: product
  actor: user
  entities:
  - entity: task
    effect: changes
    from: Pending
    to: Done
    facts:
    - Done date
  contexts:
    web:
      place: crm-web::workspace::dashboard
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/tasks/Task.tsx#Task
- kind: code
  role: implementation
  target: src/components/atomic-crm/tasks/tasksPredicate.ts#isRecentlyDone
---

# Tick a task off

## Trigger

A User has done what a task asked.

## Outcome

The task is done and leaves the upcoming tasks.
