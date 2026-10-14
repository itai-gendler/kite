---
kind: validation
routes:
  studio: Studio
steps:
- text: The Owner writes an address that is not absolute and chooses Save
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::site-settings
- text: The Product refuses the save and names the setting
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::site-settings
references:
- kind: code
  role: implementation
  target: internal/api/settings.go#checkSetting
---

# Save an invalid value

## Trigger

A value cannot be stored.

## Outcome

kite.yaml is unchanged.

## Edge cases

- Also refused: an empty title, a language that is not a language tag, an unknown time zone, more than 50 keywords, code over 64 KiB, and counts outside their range.
