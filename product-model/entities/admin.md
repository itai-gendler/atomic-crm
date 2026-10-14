---
kind: person
acts: external
relations:
- entity: user-account
  verb: holds
  cardinality: one-to-one
- entity: contact
  verb: manages
  cardinality: one-to-many
- entity: company
  verb: manages
  cardinality: one-to-many
- entity: deal
  verb: manages
  cardinality: one-to-many
- entity: task
  verb: owns
  cardinality: one-to-many
- entity: contact-note
  verb: writes
  cardinality: one-to-many
- entity: deal-note
  verb: writes
  cardinality: one-to-many
- entity: ai-agent
  verb: connects
  cardinality: one-to-many
- entity: ai-agent-access
  verb: grants
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/providers/commons/canAccess.ts#canAccess
- kind: code
  role: implementation
  target: supabase/schemas/02_functions.sql#is_admin
---

# Admin

A signed-in member of the sales team holding the Admin role. Admins do everything a User does and also manage the users of the CRM and its settings.
