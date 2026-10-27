---
type: Styleguide Rule
description: |-
  Non-leaf modules (lib.rs, mod.rs, or any module with submodules) should
  contain only module declarations and re-exports, not API implementations.
  A small amount of "ties things together" glue code is acceptable, as are
  mod tests and cross-language binding submodules.
language: rust
category: organization
rule_id: NO-IMPL-IN-NON-LEAF-MODULES
priority: warn
tags:
- organization
- modules
- google-style
---
Non-leaf modules (lib.rs, mod.rs, or any module with submodules) should
contain only module declarations and re-exports, not API implementations.
A small amount of "ties things together" glue code is acceptable, as are
mod tests and cross-language binding submodules.

## Good

- // storage/mod.rs
mod cache;
mod disk;

pub use cache::Cache;
pub use disk::DiskStore;

## Bad

- // storage/mod.rs
mod cache;
mod disk;

pub struct Index { /* 300 lines of implementation */ }
impl Index { ... }
