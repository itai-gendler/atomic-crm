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
- text: The Product lists up to ten contacts with the Hot status that the User manages
  kind: product
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts:
    - First name
    - Last name
    - Title
    - Company
    - Status
  contexts:
    web:
      place: crm-web::workspace::dashboard
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/dashboard/HotContacts.tsx
---

# See one's hot contacts on the dashboard

## Trigger

A User starts the day.

## Outcome

The User sees their hot contacts, or a hint to set a status through a note.
