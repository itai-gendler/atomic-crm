---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Postpone to tomorrow in a task's menu
  kind: actor
  actor: user
  entities:
  - entity: task
    effect: reads
    facts:
    - Description
    - Due date
  contexts:
    web:
      place: crm-web::workspace::dashboard
- text: The Product moves the task's due date to tomorrow
  kind: product
  actor: user
  entities:
  - entity: task
    effect: changes
    facts:
    - Due date
  contexts:
    web:
      place: crm-web::workspace::dashboard
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/tasks/Task.tsx#Task
---

# Postpone a task to tomorrow

## Trigger

A follow-up cannot happen today.

## Outcome

The task is listed under Tomorrow.
