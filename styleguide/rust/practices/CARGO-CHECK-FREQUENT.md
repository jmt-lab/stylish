---
type: Styleguide Rule
description: |-
  Use cargo check for fast compilation feedback without generating binaries.
  Check with --all-features to validate all feature flag combinations.
  Catch syntax and type errors early before they compound.
language: rust
category: practices
rule_id: CARGO-CHECK-FREQUENT
priority: warn
tags:
- development
- workflow
- feedback
---
Use cargo check for fast compilation feedback without generating binaries.
Check with --all-features to validate all feature flag combinations.
Catch syntax and type errors early before they compound.

## Good

- cargo check --all-features
- cargo check -p package-name

## Bad

- # Write code for hours without checking compilation
