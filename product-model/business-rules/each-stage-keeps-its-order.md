---
appliesTo:
- type: capability
  id: create-deal
- type: capability
  id: move-deal
- type: capability
  id: send-deal-back-to-board
- type: capability
  id: import-deals
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/deals/DealListContent.tsx#DealListContent
- kind: code
  role: implementation
  target: src/components/atomic-crm/deals/DealCreate.tsx#DealCreate
- kind: code
  role: implementation
  target: src/components/atomic-crm/providers/supabase/dataProvider.ts
---

# Each stage keeps its own order of deals

New deals and deals sent back to the board enter at the top of their stage; imported deals are appended at the bottom; dragging renumbers the deals around the drop, including deals hidden by filters.
