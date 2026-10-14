---
appliesTo:
- type: entity
  id: post
- type: entity
  id: page
- type: entity
  id: declared-content
references:
- kind: code
  role: implementation
  target: internal/content/content.go#IsPublic
---

# An item is public only when published and due, or scheduled and past its time

A published item with no publish time, or one that has come, is public; a scheduled item is public once its publish time has passed. Drafts, archived items, trashed items and published items dated in the future are not.
