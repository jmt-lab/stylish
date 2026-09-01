---
type: Styleguide Rule
description: |-
  If code works around a bug in external code, document what the bug
  is, what version it affects, and when it can be removed.
language: rust
category: comments
rule_id: WORKAROUND-DOCUMENTATION
priority: warn
tags:
- workarounds
- documentation
- carmack
---
If code works around a bug in external code, document what the bug
is, what version it affects, and when it can be removed.

## Good

- // Workaround for wgpu 0.18 bug with texture binding on Metal
// Can be removed once wgpu > 0.19
if cfg!(target_os = "macos") { ... }

## Bad

- // Hack for Mac
if cfg!(target_os = "macos") { ... }
