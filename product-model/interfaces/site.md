---
type: web
actors:
- reader
entryPoints:
- web: /
references:
- kind: code
  role: implementation
  target: internal/serve/server.go#Server
- kind: code
  role: implementation
  target: internal/serve/router.go#router
- kind: code
  role: implementation
  target: internal/cli/serve_cmd.go#newServeCmd
---

# Site

The site as Kite serves it itself (`kite serve`, `kite run`, the container):
every page rendered on request from the same files, templates and addresses a
build uses, so what is served is what would be published. A site built into
static files and hosted elsewhere is served by that host, not by Kite.
