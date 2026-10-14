---
appliesTo:
- type: capability
  id: publish-items
- type: entity
  id: commit
  effect: creates
references:
- kind: code
  role: implementation
  target: internal/publish/git/publisher.go#commit
- kind: code
  role: implementation
  target: internal/publish/git/preflight.go#checkPaths
---

# A publish commits exactly what it was asked to and nothing else

The paths of the items named — a post's folder, a page's file — or the paths given, and nothing else: what the owner staged stays staged and every other change stays where it is. A path git sees no change in is dropped.
