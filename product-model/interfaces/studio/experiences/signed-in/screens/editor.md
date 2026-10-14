---
entities:
- entity: post
  shows:
  - Title
  - Slug
  - Text
  - Description
  - Cover
  - Pinned
  - Categories
  - Tags
  - Publish time
  - Template
  - Aliases
  - Last saved
  collects:
  - Title
  - Slug
  - Text
  - Description
  - Cover
  - Pinned
  - Categories
  - Tags
  - Publish time
  - Template
  - Aliases
- entity: page
  shows:
  - Title
  - Slug
  - Text
  - Description
  - Menu weight
  - Publish time
  - Template
  - Aliases
  - Last saved
  collects:
  - Title
  - Slug
  - Text
  - Description
  - Menu weight
  - Publish time
  - Template
  - Aliases
- entity: declared-content
  shows:
  - Title
  - Slug
  - Text
  - Fields
  - Weight
  - Terms
  - Publish time
  - Template
  - Aliases
  - Last saved
  collects:
  - Title
  - Slug
  - Text
  - Fields
  - Weight
  - Terms
  - Publish time
  - Template
  - Aliases
- entity: content-type
  shows:
  - Label
  - Fields
  - Taxonomies
- entity: file
  shows:
  - Name
  - Link
  - Size
  - Where it is used
  - Location removed
- entity: commit
  shows:
  - Paths
  - Host
  - Live address
references:
- kind: code
  role: implementation
  target: web/src/components/editor/EditorPage.tsx#EditorPage
- kind: code
  role: implementation
  target: web/src/components/editor/PublishMenu.tsx#PublishMenu
- kind: code
  role: implementation
  target: web/src/components/editor/Attachments.tsx
- kind: code
  role: implementation
  target: web/src/components/editor/ConflictDialog.tsx
---

# Editor

One item being written: its cover, title, summary, text in the visual editor or as Markdown, its fields, terms, slug and template, its status and publish time, its files, a live preview, and how far its publishing has got.
