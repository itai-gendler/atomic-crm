---
singleton: true
domain: settings
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/root/defaultConfiguration.ts
- kind: code
  role: implementation
  target: src/components/atomic-crm/root/ConfigurationContext.tsx
- kind: code
  role: implementation
  target: supabase/schemas/01_tables.sql
---

# Settings

The CRM's shared settings, kept once for the whole team: its name and logos and the lists of values the team picks from on companies, deals, notes and tasks.

## Information kept

- **App title** — the name the CRM shows
- **Light mode logo** — the logo shown in light mode
- **Dark mode logo** — the logo shown in dark mode and on the sign-in pages
- **Currency** — the currency deal budgets are shown in
- **Company sectors** — the sectors a company can belong to
- **Deal stages** — the ordered stages of the deal pipeline, each a column of the board
- **Pipeline statuses** — the deal stages that count as pipeline deals
- **Deal categories** — the categories a deal can belong to
- **Note statuses** — the statuses, with their colours, a contact note can give a contact
- **Task types** — the types a task can have
