---
type: Styleguide Rule
description: |-
  Configure Cargo.toml release profile for optimal performance:
  lto, codegen-units=1, opt-level=3 for final builds.
language: rust
category: optimization
rule_id: RELEASE-PROFILE-TUNING
priority: warn
tags:
- optimization
- configuration
- build
---
Configure Cargo.toml release profile for optimal performance:
lto, codegen-units=1, opt-level=3 for final builds.

## Good

- [profile.release]
lto = true
codegen-units = 1
opt-level = 3

## Bad

- # Using default release profile for performance-critical code
