---
appliesTo:
- type: capability
  id: browse-tasks
  contexts:
  - place: crm-web::workspace
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/tasks/TasksListByDueDate.tsx
---

# The dashboard lists only one's own tasks

The upcoming tasks on the dashboard are the signed-in user's; a contact's page lists all of its tasks.
