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
  target: internal/publish/git/publisher.go#watched
- kind: code
  role: implementation
  target: internal/cli/publish_cmd.go#newPublishCmd
---

# Publishing every change carries only what Kite manages

Publish every change and `kite publish --all` carry the uncommitted paths under content/, static/, themes/ and plugins/, and kite.yaml and kite.lock. Templates and language packs of the site's own (layouts/, i18n/), kitew and the deploy workflows are committed by hand.
