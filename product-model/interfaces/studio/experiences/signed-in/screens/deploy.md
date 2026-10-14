---
entities:
- entity: site-settings
  shows:
  - Address
  - Pinned Kite release
  - Pinned release checksums
- entity: commit
  shows:
  - Paths
  - Branch
  - Remote
  - Host
  - Live address
- entity: github-connection
  shows:
  - Repository
  - Token comes from
  - GitHub account
  - Pages address
  collects:
  - Repository
  - Token
references:
- kind: code
  role: implementation
  target: web/src/features/deploy/index.tsx
- kind: code
  role: implementation
  target: web/src/components/publish/Delivery.tsx
---

# Deploy

How the site goes online: the export of the whole site as a zip, how far a push has got toward the site, the link to GitHub, and the Kite release the deploy builds with.
