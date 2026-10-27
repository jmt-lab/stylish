---
type: Styleguide Rule
description: |-
  Model a set of independent on/off flags with the bitflags crate (or a
  struct of named bools/enums); an enum models exactly one choice. Never pass
  raw u32 bitmasks through APIs.
language: rust
category: types
rule_id: BITFLAGS-FOR-INDEPENDENT-FLAGS
priority: info
tags:
- types
- flags
- enums
- beautiful-rust
---
Model a set of independent on/off flags with the bitflags crate (or a
struct of named bools/enums); an enum models exactly one choice. Never pass
raw u32 bitmasks through APIs.

## Good

- bitflags! {
    pub struct Permissions: u8 {
        const READ = 1 << 0;
        const WRITE = 1 << 1;
        const EXECUTE = 1 << 2;
    }
}

## Bad

- pub const READ: u32 = 1;
pub const WRITE: u32 = 2;
pub fn open(path: &Path, flags: u32) { ... }
