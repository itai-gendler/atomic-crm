---
references:
- kind: code
  role: implementation
  target: supabase/schemas/01_tables.sql
- kind: code
  role: implementation
  target: src/components/atomic-crm/tasks/TaskFormContent.tsx
---

# Task

A follow-up to do about a contact, due at a given time.

## Information kept

- **Description** — what is to be done; required
- **Type** — one of the configured task types
- **Due date** — when the task is due
- **Done date** — when the task was marked done
- **Contact** — the contact the task is about
- **Owner** — the user the task belongs to

## States

### Pending

The task is still to do.

### Done

The task is marked done.
