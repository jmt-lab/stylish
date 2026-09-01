---
type: Styleguide Rule
description: |-
  If code works around a bug in external code, hardware, or drivers,
  document what the bug is and what version/platform it affects.
language: language-agnostic
category: comments
rule_id: WORKAROUND-DOCUMENTATION
priority: error
tags:
- workarounds
- bugs
- maintenance
---
If code works around a bug in external code, hardware, or drivers,
document what the bug is and what version/platform it affects.

## Good

- // Workaround for NVIDIA driver 387.x bug with texture binding
// Can be removed once driver version > 400

## Bad

- // Hack
if (weird_condition)
