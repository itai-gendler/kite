---
appliesTo:
- type: entity
  id: post
  effect: changes
  to: Scheduled
- type: entity
  id: page
  effect: changes
  to: Scheduled
- type: entity
  id: declared-content
  effect: changes
  to: Scheduled
references:
- kind: code
  role: implementation
  target: internal/content/content.go#Validate
---

# A scheduled item always has a publish time

Saving an item as scheduled without a publish time is refused.
