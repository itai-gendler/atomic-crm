---
availability:
- place: crm-web::workspace
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/misc/useImportFromJson.ts
---

# Import from JSON

Migrate from another CRM by loading one JSON file holding users, companies, contacts, notes and tasks; tags named on contacts are matched or created.
