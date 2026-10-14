---
availability:
- place: studio::signed-in
domain: theme
references:
- kind: code
  role: implementation
  target: internal/api/previews.go#handleOpenPreview
- kind: code
  role: implementation
  target: web/src/features/settings/theme/preview-frame.tsx
---

# Preview a theme

Try a theme on the whole site before it is used: the preview is drawn with it and with its settings as they are edited, its links lead through the preview, and nothing is written until the owner saves.
