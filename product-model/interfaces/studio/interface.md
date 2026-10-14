---
type: web
actors:
- owner
- visitor
entryPoints:
- web: /admin/
languages:
- en
- zh-CN
references:
- kind: code
  role: implementation
  target: web/src/routes/__root.tsx
- kind: code
  role: implementation
  target: web/src/components/layout/data/sidebar-data.ts#useSidebarData
- kind: code
  role: implementation
  target: internal/api/api.go#routes
- kind: code
  role: implementation
  target: internal/api/auth.go#allow
- kind: doc
  role: intent
  target: docs/reference.md
  title: The studio
---

# Studio

The browser studio Kite serves at `/admin/` when it runs with the studio on
(`kite run`, or `kite serve --admin`). Everything the studio does goes through
the one HTTP API under `/api/v1`, which another client may call the same way.
Without `--write` the studio reads and previews but changes nothing. It speaks
English and Simplified Chinese, chosen from the browser.
