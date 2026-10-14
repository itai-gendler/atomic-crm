---
entities:
- entity: deal
  shows:
  - Name
  - Company
  - Budget
  - Category
  - Stage
  - Position
  - Archived on
  - Account manager
- entity: company
  shows:
  - Name
entryPoints:
- crm-web: /deals
---

# Deal board

The pipeline: a column of active deals per stage, and the archived deals.
