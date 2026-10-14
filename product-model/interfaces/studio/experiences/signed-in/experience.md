---
actors:
- owner
access: authenticated
entryPoints:
- studio: /admin/
references:
- kind: code
  role: implementation
  target: web/src/routes/_authenticated/route.tsx
- kind: code
  role: implementation
  target: internal/api/auth.go#allow
---

# Signed in

The studio itself, for the site's owner: once signed in where the site has a
password, or straight away on this computer while it has none (local mode).
