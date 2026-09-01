---
type: Styleguide Rule
description: |-
  Use cargo-outdated to find dependency updates. Keep dependencies
  reasonably current.
language: rust
category: practices
rule_id: CARGO-OUTDATED
priority: info
tags:
- practices
- maintenance
- dependencies
---
Use cargo-outdated to find dependency updates. Keep dependencies
reasonably current.

## Good

- cargo outdated

## Bad

- # Dependencies not updated in years
