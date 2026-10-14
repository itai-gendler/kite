---
entities:
- entity: site-settings
  shows:
  - Title
  - Description
  - Address
  - Language
  - Keywords
  - Time zone
  - Search engine visibility
  - Default category
  - Posts per page
  - Posts in the feed
  - Code at the end of the head
  - Code at the end of the page
  collects:
  - Title
  - Description
  - Address
  - Language
  - Keywords
  - Time zone
  - Search engine visibility
  - Default category
  - Posts per page
  - Posts in the feed
  - Code at the end of the head
  - Code at the end of the page
references:
- kind: code
  role: implementation
  target: web/src/features/settings/site/index.tsx
---

# Site settings

What the site is called and where it lives, what it tells search engines, how it reads and writes, and the code it adds to every page.
