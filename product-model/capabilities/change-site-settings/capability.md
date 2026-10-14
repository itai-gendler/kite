---
availability:
- place: studio::signed-in
references:
- kind: code
  role: implementation
  target: internal/api/settings.go#handleUpdateSettings
- kind: code
  role: implementation
  target: internal/api/settings.go#checkSetting
- kind: code
  role: implementation
  target: web/src/features/settings/site/index.tsx
---

# Change site settings

Edit what the site is called and where it lives, its language, keywords, time zone and search engine visibility, the default category, posts per page, posts in the feed, and the code added to every page (Settings → Site, Save). Written to kite.yaml, leaving everything else in it alone.
