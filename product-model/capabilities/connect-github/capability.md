---
availability:
- place: studio::signed-in
- place: cli
domain: deploy
references:
- kind: code
  role: implementation
  target: internal/publish/git/connect.go#ConnectGitHub
- kind: code
  role: implementation
  target: internal/api/github.go#handleConnectGitHub
- kind: code
  role: implementation
  target: internal/cli/github_cmd.go#newGitHubConnectCmd
- kind: doc
  role: intent
  target: docs/design/github.md
---

# Connect GitHub

Link the site to an empty repository on GitHub with a fine-grained token for it alone, under Connect GitHub on the Deploy screen or with `kite github connect owner/name`. Kite starts a git repository and adds origin where there are none, writes the deploy workflows where there are none, commits the site's own files, turns GitHub Pages on with GitHub Actions as its source and pushes. With Deploy the site with GitHub Pages off (`--no-pages`) it leaves workflows and Pages alone, for a repository another host builds.
