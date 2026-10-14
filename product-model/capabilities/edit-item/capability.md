---
availability:
- place: studio::signed-in
references:
- kind: code
  role: implementation
  target: internal/api/write.go#handleUpdate
- kind: code
  role: implementation
  target: web/src/hooks/useItem.ts#autosaves
- kind: code
  role: implementation
  target: web/src/components/editor/EditorPage.tsx#EditorPage
- kind: code
  role: implementation
  target: internal/frontmatter/frontmatter.go
---

# Edit an item

Change an item's title, text, summary, cover, terms, slug, template, aliases and fields in the editor, in the visual editor or as Markdown. A draft saves itself shortly after typing stops; any other item saves only when the owner chooses Save, since saving it changes the site. Saving rewrites only what changed in the file, keeping its key order and comments.
