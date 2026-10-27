---
type: Styleguide Rule
description: |-
  Configure lints once in Cargo.toml ([lints] or [workspace.lints] with
  [lints] workspace = true in members), not with scattered #![warn(...)]
  crate attributes. Put clippy thresholds in clippy.toml.
language: rust
category: cargo
rule_id: LINTS-IN-CARGO-TOML
priority: warn
tags:
- cargo
- lints
- clippy
- beautiful-rust
---
Configure lints once in Cargo.toml ([lints] or [workspace.lints] with
[lints] workspace = true in members), not with scattered #![warn(...)]
crate attributes. Put clippy thresholds in clippy.toml.

## Good

- [workspace.lints.rust]
unsafe_op_in_unsafe_fn = "warn"
missing_debug_implementations = "warn"

[workspace.lints.clippy]
pedantic = { level = "warn", priority = -1 }
unwrap_used = "warn"
undocumented_unsafe_blocks = "warn"

## Bad

- // lib.rs
#![warn(clippy::pedantic)]
#![warn(clippy::unwrap_used)] // repeated differently in every crate
