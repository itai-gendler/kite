---
appliesTo:
- type: capability
  id: publish-items
- type: capability
  id: push-commits
references:
- kind: code
  role: implementation
  target: internal/publish/git/lock.go
---

# One publish or push runs at a time

A publish or a push started while another is under way is refused, so two cannot interleave a commit.
