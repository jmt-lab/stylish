---
type: Styleguide Rule
description: |-
  Use idiomatic Rust patterns that the community expects.
  This makes code more maintainable.
language: rust
category: practices
rule_id: COMMUNITY-STANDARDS
priority: info
tags:
- practices
- idioms
- official
---
Use idiomatic Rust patterns that the community expects.
This makes code more maintainable.

## Good

- // Idiomatic error handling
fn load() -> Result<Data, Error> { ... }

## Bad

- // Non-idiomatic
fn load() -> (Data, bool) // tuple for errors
