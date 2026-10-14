---
availability:
- place: site
references:
- kind: code
  role: implementation
  target: internal/serve/server.go#Server
- kind: code
  role: implementation
  target: internal/serve/router.go#router
---

# Read the site

Read the pages Kite serves: the home page, posts, pages, listings, tag and category pages, the feed and the sitemap, rendered on request from the same files a build uses, and re-planned when a scheduled item falls due.
