---
singleton: true
references:
- kind: code
  role: implementation
  target: internal/serve/server.go#Options
- kind: code
  role: implementation
  target: internal/cli/serve_cmd.go#serveCommand
- kind: code
  role: implementation
  target: internal/serve/server.go#NewWithClock
---

# Studio server

How the running Kite server was started, which decides what its studio and its site may do. It is chosen when the server starts — `kite run`, `kite serve` and their flags, or the container — and holds until it stops.

## Information kept

- **Studio served** — whether the studio and its API are served (--admin; on for kite run)
- **Changes allowed** — whether the studio may change the site (--write; on for kite run); without it the studio reads and previews only
- **Drafts included** — whether the site it serves shows drafts (--drafts; on for kite run)
- **Reachable from other machines** — whether it listens on an address other than this computer's
- **Waiting for setup** — whether it is waiting for its setup: reachable from other machines with no account, or started in an empty folder to create a site there
