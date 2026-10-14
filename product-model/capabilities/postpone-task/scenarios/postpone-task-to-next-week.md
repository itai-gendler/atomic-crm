---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Postpone to next week in a task's menu
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
- text: The Product moves the task's due date seven days ahead
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

# Postpone a task to next week

## Trigger

A follow-up can wait a week.

## Outcome

The task is due a week from today.
