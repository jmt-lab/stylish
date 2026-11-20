---
type: Styleguide Rule
description: |-
  For published library crates, make the README the crate-level docs with
  #![doc = include_str!("../README.md")], so its examples run as doctests
  and the two can't drift apart.
language: rust
category: documentation
rule_id: CRATE-README-AS-DOCS
priority: info
tags:
- documentation
- readme
- doctests
- rust-skills
---
For published library crates, make the README the crate-level docs with
#![doc = include_str!("../README.md")], so its examples run as doctests
and the two can't drift apart.

## Good

- // src/lib.rs
#![doc = include_str!("../README.md")]

## Bad

- // src/lib.rs
//! A fast CSV parser. (README.md has different, untested examples.)
