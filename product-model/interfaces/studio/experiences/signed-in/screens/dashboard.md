---
entities:
- entity: post
  shows:
  - Title
  - Publish time
  - Categories
  - Tags
- entity: commit
  shows:
  - Paths
  - Branch
  - Remote
  - Host
  - Live address
- entity: term
  shows:
  - Name
  - Count
references:
- kind: code
  role: implementation
  target: web/src/features/dashboard/index.tsx
- kind: code
  role: implementation
  target: web/src/features/dashboard/components/cards.tsx#DeliveryOverview
---

# Dashboard

The site at a glance: how many posts are drafts and scheduled, the latest posts published, the top tags and categories, a publishing trend by month, and how far content has travelled from saved to deployed, with what is still uncommitted.
