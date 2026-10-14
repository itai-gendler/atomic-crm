---
appliesTo:
- type: capability
  id: archive-deal
- type: capability
  id: browse-deals
- type: capability
  id: search-crm
references:
- kind: code
  role: implementation
  target: src/components/atomic-crm/deals/DealList.tsx
- kind: code
  role: implementation
  target: supabase/schemas/08_search.sql
---

# Archived deals are off the board and out of search

Only active deals appear on the board; archived deals are listed apart, and global search leaves out archived deals and their notes.
