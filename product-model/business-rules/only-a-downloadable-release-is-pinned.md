---
appliesTo:
- type: capability
  id: pin-kite-release
  contexts:
  - place: studio::signed-in
  - place: cli
references:
- kind: code
  role: implementation
  target: internal/api/kite.go#handlePin
- kind: code
  role: implementation
  target: internal/cli/wrapper_cmd.go#releaseToPin
---

# Only a Kite release that can be downloaded is pinned

A build from source, or a release whose archives cannot be found, is not pinned, since every build through kitew would fail on it.
