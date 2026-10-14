---
availability:
- place: studio::signed-in
domain: deploy
references:
- kind: code
  role: implementation
  target: internal/api/export.go#handleExport
- kind: code
  role: implementation
  target: internal/serve/server.go#export
- kind: code
  role: implementation
  target: web/src/features/deploy/index.tsx
---

# Export the site

Build every page of the site into static files and download them as a zip to upload to any host, from the Deploy screen. The export is the site a deployment gets, whatever the server shows; it is offered on a server that does not allow changes too.
