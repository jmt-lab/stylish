---
type: Styleguide Rule
description: |-
  Never put #![deny(warnings)] in source. New toolchains add warnings and
  break the build for every downstream user. Enforce warnings-as-errors in CI
  (cargo clippy -- -D warnings) or deny specific lints by name.
language: rust
category: practices
rule_id: NO-DENY-WARNINGS-IN-SOURCE
priority: error
tags:
- practices
- lints
- ci
- beautiful-rust
---
Never put #![deny(warnings)] in source. New toolchains add warnings and
break the build for every downstream user. Enforce warnings-as-errors in CI
(cargo clippy -- -D warnings) or deny specific lints by name.

## Good

- cargo clippy --all-targets --all-features -- -D warnings  # in CI

## Bad

- // lib.rs
#![deny(warnings)]
