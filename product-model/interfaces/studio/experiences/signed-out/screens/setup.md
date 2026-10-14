---
entities:
- entity: site-settings
  collects:
  - Title
  - Address
  - Language
  - Author
- entity: account
  collects:
  - User name
  - Password
references:
- kind: code
  role: implementation
  target: web/src/features/auth/setup/index.tsx
---

# Set up

Where a server nobody has configured is set up, or a new site is created in an empty folder: the site's description first, then the account that will guard it on a server.
