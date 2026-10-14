---
kind: configuration
of: business-rule
settings:
- {entity: studio-server, fact: Drafts included}
takesEffect: 'When a server starts or a build runs: kite run includes drafts, kite serve and kite build
  leave them out, and --drafts says otherwise for any of them.'
stability: Fixed for the life of the server or the build. An export from a server that includes drafts
  still leaves them out.
alternatives:
- id: site-shows-public-items-only
  selectedWhen: 'Drafts included is off: kite serve, the container and kite build unless --drafts is given.'
- id: preview-shows-drafts
  selectedWhen: 'Drafts included is on: kite run unless --drafts=false is given, or kite serve or kite
    build with --drafts.'
references:
- kind: code
  role: implementation
  target: internal/cli/serve_cmd.go#serveCommand
- kind: code
  role: implementation
  target: internal/serve/server.go#Options
---

# Drafts on the site

A site served for local writing shows drafts so the owner can read it whole,
while a site served or built for readers shows only what is public; both are
supported.
