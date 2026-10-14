---
appliesTo:
- type: capability
  id: import-hexo
  contexts:
  - place: cli
references:
- kind: code
  role: implementation
  target: internal/importer/hexo/hexo.go
---

# Every address Hexo published a post or page at keeps leading to it

Each becomes an alias of the imported item, so links to the old site keep working; the Hexo site itself is left as it is.
