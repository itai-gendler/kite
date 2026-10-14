---
appliesTo:
- type: capability
  id: build-site
  contexts:
  - place: cli
references:
- kind: code
  role: implementation
  target: internal/site/output.go
---

# A build replaces only an output folder of its own

A folder that already holds files is replaced only when a build of this project wrote it, or it holds this site's sitemap or feed; a file, the project or any of its own folders is refused.
