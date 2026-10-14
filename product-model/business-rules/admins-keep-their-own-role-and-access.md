---
appliesTo:
- type: capability
  id: revoke-admin-role
- type: capability
  id: disable-user
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/sales/SalesInputs.tsx#SalesInputs
---

# An Admin never revokes their own Admin role or disables their own account

On an Admin's own account the Admin and Disabled switches are read-only, so the CRM never loses its last Admin by accident.
