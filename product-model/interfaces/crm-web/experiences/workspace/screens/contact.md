---
entities:
- entity: contact
  shows:
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
  - Avatar
  - First seen
  - Last seen
  - Pending tasks
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
  - Status
- entity: contact-note
  shows:
  - Text
  - Date
  - Status
  - Attachments
  - Author
  collects:
  - Text
  - Date
  - Status
  - Attachments
- entity: task
  shows:
  - Description
  - Type
  - Due date
  - Done date
  collects:
  - Description
  - Type
  - Due date
  - Contact
- entity: tag
  shows:
  - Name
  - Color
entryPoints:
- crm-web: /contacts/:id/show
---

# Contact

One contact: its details, notes, tasks and tags, viewed or edited.
