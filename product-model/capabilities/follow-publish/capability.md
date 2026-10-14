---
availability:
- place: studio::signed-in
references:
- kind: code
  role: implementation
  target: internal/publish/git/publisher.go#State
- kind: code
  role: implementation
  target: internal/publish/git/publisher.go#deployed
- kind: code
  role: implementation
  target: internal/publish/git/deploy.go#newDeployChecker
- kind: code
  role: implementation
  target: internal/publish/git/site.go#publicAddress
- kind: code
  role: implementation
  target: web/src/components/publish/Delivery.tsx
- kind: doc
  role: intent
  target: docs/reference.md
  title: Static, to GitHub Pages
---

# Follow a publish

See how far content has travelled — saved, committed, pushed, deployed — on the dashboard, the Deploy screen and the editor's publishing panel. Once a commit is pushed, the Product asks the site at its address which commit it was built from, and, for a repository on GitHub, what the host recorded, until the commit is live or the host reports a failure.
