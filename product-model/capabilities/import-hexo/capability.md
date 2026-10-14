---
availability:
- place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/import_cmd.go#newImportHexoCmd
- kind: code
  role: implementation
  target: internal/importer/hexo/hexo.go
- kind: doc
  role: intent
  target: docs/reference.md
  title: Moving from Hexo
---

# Import a Hexo site

`kite import hexo <hexo-site> [dir]` reads a Hexo site's posts, drafts, pages and files into a Kite project and leaves the Hexo site as it is. An empty or missing folder becomes a new project named, addressed and dated as the Hexo site is; a Kite project gets the content added to its own. Every address Hexo published a post or page at keeps leading to it.
