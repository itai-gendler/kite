---
availability:
- place: studio::signed-in
references:
- kind: code
  role: implementation
  target: web/src/features/terms/term-dialog.tsx
- kind: code
  role: implementation
  target: internal/api/terms.go#changeTerm
---

# Merge a term into another

Fold one tag or category into another; only the one chosen remains, and an item that carried both keeps it once.
