---
entities:
- entity: company
  shows:
  - Name
- entity: contact
  shows:
  - First name
- entity: deal
  shows:
  - Name
  collects:
  - Name
  - Description
  - Company
  - Contacts
  - Category
  - Budget
  - Expected closing date
  - Stage
  - Account manager
entryPoints:
- crm-web: /deals/create
---

# New deal

Where a deal is entered.
