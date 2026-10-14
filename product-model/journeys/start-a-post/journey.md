---
actors:
- owner
references:
- kind: code
  role: implementation
  target: web/src/components/editor/EditorPage.tsx#EditorPage
- kind: code
  role: implementation
  target: web/src/hooks/useItem.ts#useItem
---

# Start a post

## Goal

Begin a new post and go on writing it as a saved draft.

## Success criterion

The new post exists as a draft and the editor goes on with it at its own address, saving as the owner writes.
