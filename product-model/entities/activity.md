---
references:
- kind: code
  role: implementation
  target: supabase/schemas/03_views.sql
- kind: code
  role: implementation
  target: src/components/atomic-crm/activity/ActivityLog.tsx#ActivityLog
---

# Activity

The activity log: an entry for each company, contact, note and deal added, shown newest first on the dashboard and on each company.

## Information kept

- **Event** — what was added: a company, a contact, a contact note, a deal or a deal note
- **Date** — when it was added
- **Added by** — the user who added it
- **Company** — the company it concerns
- **Record** — the added record, as it reads now
