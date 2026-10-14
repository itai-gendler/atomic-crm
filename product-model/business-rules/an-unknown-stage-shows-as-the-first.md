---
appliesTo:
- type: capability
  id: browse-deals
- type: capability
  id: import-deals
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/deals/stages.ts#getDealsByStage
- kind: code
  role: implementation
  target: src/components/atomic-crm/dataImport/useDealImport.ts
---

# A deal whose stage is not configured shows in the first stage

The board puts a deal with no matching configured stage in the first column, and imported deals with an empty or unknown stage get the first stage.
