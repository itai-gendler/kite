---
appliesTo:
- type: capability
  id: rename-term
- type: capability
  id: merge-term
- type: capability
  id: remove-term
references:
- kind: code
  role: implementation
  target: internal/api/terms.go#carriers
- kind: code
  role: implementation
  target: internal/api/terms.go#changeTerm
---

# A term is renamed, merged or deleted on every item that carries it, trashed ones included

The change is written to every item carrying the term in any of its spellings, in one change set, and only if none of them changed since the term was read.
