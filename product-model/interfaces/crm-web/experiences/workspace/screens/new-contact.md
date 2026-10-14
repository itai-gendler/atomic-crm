---
entities:
- entity: company
  shows:
  - Name
  collects:
  - Name
  - Account manager
- entity: contact
  shows:
  - First name
  collects:
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
  - Tags
entryPoints:
- crm-web: /contacts/create
---

# New contact

Where a contact is entered.
