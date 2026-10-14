---
appliesTo:
- type: capability
  id: publish-items
  contexts:
  - place: studio::signed-in
  - place: cli
references:
- kind: code
  role: implementation
  target: internal/publish/git/publisher.go#commit
- kind: code
  role: implementation
  target: internal/publish/publish.go#Request
---

# A repository's commit hooks run on every publish unless the owner skips them after a refusal

Skipping the hooks is offered only once a hook's refusal has been shown (Publish without the hooks, `kite publish --no-verify`); a refused publish leaves the repository as it found it.

## Rationale

A hook is the repository owner's rule.
