---
domain: deals
availability:
- place: crm-web::workspace
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/deals/DealList.tsx
- kind: code
  role: implementation
  target: src/components/atomic-crm/deals/DealListContent.tsx#DealListContent
---

# Browse deals

See the active deals on the board, one column per configured stage with its total budget, narrowed by name, company, category or account manager, and look up archived deals.
