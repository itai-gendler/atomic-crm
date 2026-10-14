---
domain: companies
availability:
- place: crm-web::workspace
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/companies/CompanyCreate.tsx#CompanyCreate
---

# Create company

Add an organisation. Its website gains https:// when typed without it, and its logo is taken from the website when none is uploaded.
