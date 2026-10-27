---
type: Styleguide Rule
description: |-
  Cargo features must be additive: any combination compiles, and enabling
  a feature never removes or changes a public item. Use a std feature on a
  no_std base, never a no-std feature. Don't feature-gate struct fields or
  trait methods.
language: rust
category: cargo
rule_id: ADDITIVE-FEATURES
priority: error
tags:
- cargo
- features
- semver
- beautiful-rust
---
Cargo features must be additive: any combination compiles, and enabling
a feature never removes or changes a public item. Use a std feature on a
no_std base, never a no-std feature. Don't feature-gate struct fields or
trait methods.

## Good

- [features]
default = ["std"]
std = []
serde = ["dep:serde"]

## Bad

- [features]
no-std = []          # subtractive
legacy-api = []      # changes signatures of existing functions
