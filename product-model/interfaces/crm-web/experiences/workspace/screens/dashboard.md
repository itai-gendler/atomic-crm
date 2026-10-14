---
entities:
- entity: contact
  shows:
  - First name
  - Last name
  - Title
  - Company
  - Status
- entity: task
  shows:
  - Description
  - Type
  - Due date
  - Done date
  - Contact
  - Owner
  collects:
  - Description
  - Type
  - Due date
  - Contact
- entity: activity
  shows:
  - Event
  - Date
  - Added by
  - Company
  - Record
entryPoints:
- crm-web: /
---

# Dashboard

The signed-in home: hot contacts, latest activity and upcoming tasks, or the getting-started steps in a new CRM.
