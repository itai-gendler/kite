---
availability:
- place: studio::signed-in
- place: cli
references:
- kind: code
  role: implementation
  target: internal/api/publish.go#handlePublish
- kind: code
  role: implementation
  target: internal/publish/git/preflight.go#preflight
- kind: code
  role: implementation
  target: internal/publish/git/publisher.go#Apply
- kind: code
  role: implementation
  target: web/src/hooks/usePublish.ts#usePublish
- kind: code
  role: implementation
  target: internal/cli/publish_cmd.go#newPublishCmd
- kind: doc
  role: intent
  target: docs/reference.md
  title: Deploying
---

# Publish

Commit the items named, or every uncommitted change Kite manages, and push the commit to the repository's remote, so whatever builds the site from the repository deploys it. In the studio, while the site publishes with Git and the server allows changes: Publish (Update for a published item) in the editor, Publish on items selected in a list, Publish every change on the dashboard and the Deploy screen, and Publish on the settings screens for kite.yaml, kite.lock, themes, plugins and uploads. From the command line, `kite publish` commits the paths given, or `--all`, and pushes with `--push`. Publishing never changes an item's status.
