---
entities:
- entity: deal
  shows:
  - Name
  - Description
  - Company
  - Contacts
  - Category
  - Budget
  - Expected closing date
  - Stage
  - Archived on
  collects:
  - Name
  - Description
  - Company
  - Contacts
  - Category
  - Budget
  - Expected closing date
  - Stage
- entity: deal-note
  shows:
  - Text
  - Date
  - Attachments
  - Author
  collects:
  - Text
  - Date
  - Attachments
entryPoints:
- crm-web: /deals/:id/show
---

# Deal

One deal: its details and notes, viewed or edited.
