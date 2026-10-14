---
appliesTo:
- type: capability
  id: publish-items
- type: capability
  id: push-commits
references:
- kind: code
  role: implementation
  target: internal/publish/git/publisher.go#push
- kind: code
  role: implementation
  target: internal/publish/publish.go#RemoteChange
---

# A push is never forced

When the remote has commits the branch does not, the push is refused and the commit stays on the branch; the remote's commits are listed, and are never merged on the owner's behalf.
