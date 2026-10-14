---
availability:
- place: studio::signed-in
- place: cli
references:
- kind: code
  role: implementation
  target: internal/api/write.go#handleCreate
- kind: code
  role: implementation
  target: web/src/hooks/useItem.ts#autosaves
- kind: code
  role: implementation
  target: web/src/hooks/useItem.ts#useItem
- kind: doc
  role: intent
  target: docs/reference.md
---

# Create an item

Start a new post, page or item of a kind the site declares, from its list (New post) or the dashboard (Write a post). The editor opens on an unsaved draft; the first save — the owner's, or the draft's own once it has a title or some text — creates it, and the editor moves to its own address. From the command line, `kite new <kind> <title>` creates one, published unless --draft.
