---
kind: primary
routes:
  web: Web
steps:
- text: The User opens Contacts
  kind: actor
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::contacts
- text: The Product lists contacts with their company, status, tags, pending tasks and when they were last seen, most recently seen first
  kind: product
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts:
    - First name
    - Last name
    - Avatar
    - Title
    - Company
    - Status
    - Tags
    - Pending tasks
    - Last seen
  - entity: tag
    effect: reads
    facts:
    - Name
    - Color
  - entity: company
    effect: reads
    facts: []
  - entity: task
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::contacts
- text: The User searches by name or company and picks filters such as Today, Hot, a tag, With pending tasks or Me
  kind: actor
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts:
    - Last seen
    - Status
    - Tags
    - Pending tasks
    - Account manager
  - entity: company
    effect: reads
    facts: []
  - entity: task
    effect: reads
    facts: []
  - entity: tag
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::contacts
- text: The Product lists only the matching contacts
  kind: product
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts:
    - First name
    - Last name
  contexts:
    web:
      place: crm-web::workspace::contacts
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/contacts/ContactList.tsx#ContactList
- kind: code
  role: implementation
  target: src/components/atomic-crm/contacts/ContactListFilter.tsx#ContactListFilter
---

# Browse and filter contacts

## Trigger

A User looks for contacts to follow up.

## Outcome

The User sees the contacts matching every chosen filter.

## Edge cases

- Only an Admin can also filter by another user as account manager; other users filter by Me.
- The mobile list has no search box of its own; global search finds contacts there.
