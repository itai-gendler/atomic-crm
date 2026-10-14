---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Export to vCard on a contact's page
  kind: actor
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::contact
- text: The Product downloads the contact as a vCard
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
    - Email addresses
    - Phone numbers
    - LinkedIn URL
    - Avatar
  contexts:
    web:
      place: crm-web::workspace::contact
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/contacts/ExportVCardButton.tsx
---

# Export a contact to vCard

## Trigger

A User wants the contact in their address book.

## Outcome

The User has the contact's vCard.
