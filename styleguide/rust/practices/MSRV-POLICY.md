---
type: Styleguide Rule
description: Document MSRV in Cargo.toml and README. Test against it in CI.
language: rust
category: practices
rule_id: MSRV-POLICY
priority: warn
tags:
- practices
- compatibility
- versioning
---
Document MSRV in Cargo.toml and README. Test against it in CI.

## Good

- [package]
rust-version = "1.70"

## Bad

- # MSRV unknown, breaks for users with older Rust
