---
domain: companies
availability:
- place: crm-web::workspace
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/companies/CompanyAside.tsx#CompanyAside
---

# Delete company

Remove a company together with every contact working at it and every deal made with it, and their notes and tasks.
