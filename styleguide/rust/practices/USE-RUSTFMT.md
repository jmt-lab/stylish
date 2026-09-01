---
type: Styleguide Rule
description: |-
  Run rustfmt on all code. Configure in rustfmt.toml if needed.
  Formatting should be automated, not debated.
language: rust
category: practices
rule_id: USE-RUSTFMT
priority: error
tags:
- practices
- formatting
- official
---
Run rustfmt on all code. Configure in rustfmt.toml if needed.
Formatting should be automated, not debated.

## Good

- cargo fmt --all

## Bad

- # Manual formatting, inconsistent style
