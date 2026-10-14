---
appliesTo:
- type: capability
  id: check-project
  contexts:
  - place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/commands.go#newDoctorCmd
---

# Two items carrying one id are reported, never repaired

Only the owner knows which copy should keep the identity.
