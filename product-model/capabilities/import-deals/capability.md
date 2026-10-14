---
domain: deals
availability:
- place: crm-web::workspace
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/dataImport/useDealImport.ts
---

# Import deals

Load deals from a CSV file in the background, matching or creating their companies and matching category and stage to the configured ones.
