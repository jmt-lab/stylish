---
type: Styleguide Rule
description: |-
  Always run tests before committing. Consider using a pre-commit
  hook to enforce this.
language: rust
category: practices
rule_id: CARGO-TEST-ALWAYS
priority: error
tags:
- practices
- testing
---
Always run tests before committing. Consider using a pre-commit
hook to enforce this.

## Good

- cargo test --all-features

## Bad

- # Commit without testing
