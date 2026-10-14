---
entities:
- entity: contact
  shows:
  - First name
  - Last name
  - Avatar
  - Title
  - Company
  - Status
  - Tags
  - Pending tasks
  - Last seen
  - Account manager
- entity: tag
  shows:
  - Name
  - Color
- entity: company
  shows:
  - Name
- entity: task
  shows:
  - Description
entryPoints:
- crm-web: /contacts
---

# Contacts

The list of contacts with its filters and bulk actions.
