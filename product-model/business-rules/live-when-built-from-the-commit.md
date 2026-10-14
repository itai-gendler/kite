---
appliesTo:
- type: capability
  id: follow-publish
  contexts:
  - place: studio::signed-in
references:
- kind: code
  role: implementation
  target: internal/publish/git/publisher.go#deployed
- kind: code
  role: implementation
  target: internal/stamp/stamp.go
---

# A commit is live when the site was built from it or from a later commit containing it

The site's own kite-build.json is the better witness, since it is what readers are served; only the host can say a deployment failed.
