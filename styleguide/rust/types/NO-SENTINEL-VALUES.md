---
type: Styleguide Rule
description: |-
  Represent "no value" with Option, never sentinels like -1, 0, u32::MAX,
  or an empty string.
language: rust
category: types
rule_id: NO-SENTINEL-VALUES
priority: error
tags:
- types
- option
- type-safety
- beautiful-rust
---
Represent "no value" with Option, never sentinels like -1, 0, u32::MAX,
or an empty string.

## Good

- pub fn find(&self, name: &str) -> Option<usize> { ... }
- pub struct User { nickname: Option<String> }

## Bad

- pub fn find(&self, name: &str) -> isize { ... } // -1 when missing
- pub struct User { nickname: String } // "" means none
