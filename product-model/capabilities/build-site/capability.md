---
availability:
- place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/build_cmd.go#newBuildCmd
- kind: code
  role: implementation
  target: internal/site/output.go
- kind: doc
  role: intent
  target: docs/reference.md
  title: Configuration
---

# Build the site

`kite build` writes the static site — what a deployment publishes — into build.output (public/ unless set) or --output, leaving drafts out unless --drafts. It says when the next scheduled post falls due, and --verify builds twice and fails if any byte differs. The deploy workflows Kite writes run it through kitew.
