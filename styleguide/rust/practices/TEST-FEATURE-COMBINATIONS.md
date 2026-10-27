---
type: Styleguide Rule
description: |-
  CI should build and test the feature combinations that matter (e.g. with
  cargo hack --feature-powerset or --each-feature), plus every
  platform-specific code path, not just --all-features.
language: rust
category: practices
rule_id: TEST-FEATURE-COMBINATIONS
priority: info
tags:
- practices
- ci
- features
- testing
- beautiful-rust
---
CI should build and test the feature combinations that matter (e.g. with
cargo hack --feature-powerset or --each-feature), plus every
platform-specific code path, not just --all-features.

## Good

- cargo hack test --each-feature --no-dev-deps

## Bad

- cargo test --all-features  # the only CI job; --no-default-features never built
