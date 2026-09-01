---
type: Styleguide Rule
description: |-
  Library crates should provide usage examples in examples/
  directory. Each example is a separate binary.
language: rust
category: organization
rule_id: EXAMPLES-DIRECTORY
priority: info
tags:
- organization
- examples
- documentation
---
Library crates should provide usage examples in examples/
directory. Each example is a separate binary.

## Good

- examples/
  basic.rs
  advanced.rs

## Bad

- // No examples for library users
