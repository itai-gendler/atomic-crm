---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Edit contact and changes the contact's details
  kind: actor
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::contact
- text: The Product saves the contact and shows its page
  kind: product
  actor: user
  entities:
  - entity: contact
    effect: changes
    facts:
    - First name
    - Last name
    - Gender
    - Title
    - Company
    - Email addresses
    - Phone numbers
    - LinkedIn URL
    - Background
    - Has newsletter
    - Account manager
    - Avatar
  contexts:
    web:
      place: crm-web::workspace::contact
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/contacts/ContactEdit.tsx#ContactEdit
- kind: code
  role: implementation
  target: src/components/atomic-crm/contacts/ContactInputs.tsx#ContactInputs
---

# Edit a contact

## Trigger

A contact changes job, address or phone.

## Outcome

The contact page shows the new details.
