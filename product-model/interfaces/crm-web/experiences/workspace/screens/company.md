---
entities:
- entity: company
  shows:
  - Name
  - Logo
  - Sector
  - Size
  - Website
  - LinkedIn URL
  - Phone number
  - Address
  - City
  - Zip code
  - State
  - Country
  - Description
  - Context links
  - Revenue
  - Tax identifier
  - Account manager
  - Added on
  - Number of contacts
  - Number of deals
  collects:
  - Name
  - Sector
  - Size
  - Website
  - LinkedIn URL
  - Phone number
  - Address
  - City
  - Zip code
  - State
  - Country
  - Description
  - Context links
  - Revenue
  - Tax identifier
  - Account manager
- entity: contact
  shows:
  - First name
  - Last name
  - Title
  - Pending tasks
  - Tags
  - Last seen
  - Status
- entity: deal
  shows:
  - Name
  - Stage
  - Budget
  - Category
  - Last activity
- entity: activity
  shows:
  - Event
  - Date
  - Added by
  - Record
entryPoints:
- crm-web: /companies/:id/show
---

# Company

One company: its details, activity, contacts and deals, viewed or edited.
