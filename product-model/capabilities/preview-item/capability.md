---
availability:
- place: studio::signed-in
references:
- kind: code
  role: implementation
  target: internal/api/preview.go#handlePreview
- kind: code
  role: implementation
  target: web/src/components/editor/Preview.tsx
---

# Preview an item

Draw the item being edited, saved or not, as the site would show it, with the active theme and the plugins that are on, beside the editor at desktop or phone width.
