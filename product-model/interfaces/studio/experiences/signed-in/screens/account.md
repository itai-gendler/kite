---
entities:
- entity: account
  shows:
  - User name
  - Comes from
  - Email
  - Picture
  collects:
  - User name
  - Password
  - Email
- entity: site-settings
  shows:
  - Author
  collects:
  - Author
- entity: session
  shows:
  - Expires
  - Remembered
references:
- kind: code
  role: implementation
  target: web/src/features/settings/account/index.tsx
---

# Account

The owner's name, picture and email, the name and password the studio signs in with, and the browsers signed in.
