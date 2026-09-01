---
type: Styleguide Rule
description: |-
  CI should fail on warnings. Add RUSTFLAGS=\"-D warnings\" to
  prevent merging code with warnings.
language: rust
category: practices
rule_id: DENY-WARNINGS-CI
priority: error
tags:
- practices
- ci
- enforcement
---
CI should fail on warnings. Add RUSTFLAGS=\"-D warnings\" to
prevent merging code with warnings.

## Good

- # .github/workflows/ci.yml
RUSTFLAGS: -D warnings

## Bad

- # CI allows warnings to pass
