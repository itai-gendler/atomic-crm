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
- text: The Product lists the latest additions across the CRM, newest first, loading more on demand
  kind: product
  actor: user
  entities:
  - entity: activity
    effect: reads
    facts:
    - Event
    - Date
    - Added by
    - Company
    - Record
  contexts:
    web:
      place: crm-web::workspace::dashboard
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/dashboard/DashboardActivityLog.tsx
- kind: code
  role: implementation
  target: src/components/atomic-crm/activity/ActivityLog.tsx#ActivityLog
- kind: code
  role: implementation
  target: src/components/atomic-crm/dashboard/Dashboard.tsx#Dashboard
---

# See the latest activity on the dashboard

## Trigger

A User catches up on the team's work.

## Outcome

The User sees who added what, and when.

## Edge cases

- Until the CRM has a contact and a contact note, the dashboard shows the getting-started steps instead.
