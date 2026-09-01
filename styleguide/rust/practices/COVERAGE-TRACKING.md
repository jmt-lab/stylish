---
type: Styleguide Rule
description: |-
  Use cargo-tarpaulin or cargo-llvm-cov to measure test coverage.
  Aim for high coverage of critical paths.
language: rust
category: practices
rule_id: COVERAGE-TRACKING
priority: info
tags:
- practices
- testing
- coverage
---
Use cargo-tarpaulin or cargo-llvm-cov to measure test coverage.
Aim for high coverage of critical paths.

## Good

- cargo tarpaulin --out Html

## Bad

- # No coverage measurement
