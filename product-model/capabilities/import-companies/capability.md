---
domain: companies
availability:
- place: crm-web::workspace
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/dataImport/useCompanyImport.ts
---

# Import companies

Load companies from a CSV file in the background; sectors are matched to the configured sectors by value or label.
