---
entities:
- entity: post
  shows:
  - Title
  - Publish time
  - Categories
  - Tags
  - Pinned
  - Deleted at
- entity: page
  shows:
  - Title
  - Publish time
  - Deleted at
- entity: declared-content
  shows:
  - Title
  - Publish time
  - Weight
  - Terms
  - Deleted at
- entity: content-type
  shows:
  - Label
  - Taxonomies
references:
- kind: code
  role: implementation
  target: web/src/features/contents/index.tsx
- kind: code
  role: implementation
  target: web/src/features/contents/components/contents-columns.tsx
---

# Content list

The items of one kind — posts, pages or another declared kind — searched and filtered by status, term and date through the index, with the trash as one of its filters; items are opened, published, deleted and restored from here, one or several at once.
