---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Export on the contact list, or on a selection
  kind: actor
  actor: user
  entities:
  - entity: contact
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::contacts
- text: The Product downloads a CSV of those contacts with company, account manager, tags, emails and phones by type
  kind: product
  actor: user
  entities:
  - entity: contact
    effect: reads
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
    - Status
    - Tags
    - First seen
    - Last seen
  - entity: company
    effect: reads
    facts: []
  - entity: tag
    effect: reads
    facts: []
  contexts:
    web:
      place: crm-web::workspace::contacts
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/contacts/ContactList.tsx#ContactList
---

# Export contacts to CSV

## Trigger

A User needs contacts outside the CRM.

## Outcome

The User has a contacts CSV file.
