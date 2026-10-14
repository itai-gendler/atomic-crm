---
id: atomic-crm
summary: 'A full-featured, open-source CRM for small sales teams: contacts, companies, a Kanban deal pipeline, notes, tasks, email capture and an MCP server.'
category: crm
tags:
- crm
- sales
- pipeline
- contacts
authors:
- name: Marmelab
  url: https://marmelab.com
license: MIT
languages:
- en
- fr
limitations:
- All signed-in users share one set of contacts, companies, deals, notes and tasks.
- Users are never deleted; an Admin disables an account instead.
- Only the first account is created by signing up; every later user is created by an Admin.
- People sign in with an email and password or, where configured, through Google Workspace single sign-on.
- Emails reach the CRM only through an external inbound email service.
references:
- kind: doc
  role: intent
  target: README.md
- kind: doc
  role: intent
  target: doc/src/content/docs/index.mdx
- kind: code
  role: context
  target: src/components/atomic-crm/root/CRM.tsx#CRM
---

# Atomic CRM

A CRM for a sales team: it keeps the team's contacts and the companies they work at, moves deals through a pipeline of stages on a Kanban board, and records the notes and tasks that follow each conversation. Emails copied to the CRM become notes, data comes in and out as CSV, JSON and vCard, and a person's AI assistant can work the same data through an MCP server. Admins manage the team's accounts and the CRM's shared settings.

## Intent

Atomic CRM is a full-featured CRM that is free and open-source and easy to customize: organize contacts, create tasks and set reminders, take notes, capture emails by copying the CRM, visualize and track the sales pipeline in a Kanban board, import and export data, control access, track activity history and integrate through an API. Its code is intentionally small so that a team can fork it and adapt the data model, the lists of values and the look to its own needs.
