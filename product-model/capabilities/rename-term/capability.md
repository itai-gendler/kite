---
availability:
- place: studio::signed-in
references:
- kind: code
  role: implementation
  target: internal/api/terms.go#handleRenameTerm
- kind: code
  role: implementation
  target: internal/api/terms.go#changeTerm
---

# Rename a term

Write a new name for a tag or category on every item that carries it, however each wrote it — trashed items included. Renaming it to its own name writes it one way.
