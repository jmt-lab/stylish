---
type: Styleguide Rule
description: |-
  When a panicking convenience API is justified, also offer a fallible
  counterpart (get / index, try_new / new, checked_add / +) and document the
  panic under # Panics.
language: rust
category: error_handling
rule_id: PAIR-PANICKING-WITH-FALLIBLE
priority: info
tags:
- error-handling
- panics
- api-design
- beautiful-rust
---
When a panicking convenience API is justified, also offer a fallible
counterpart (get / index, try_new / new, checked_add / +) and document the
panic under # Panics.

## Good

- /// # Panics
///
/// Panics if `index` is out of bounds. See [`Self::get`] for a fallible version.
pub fn at(&self, index: usize) -> &T { ... }
pub fn get(&self, index: usize) -> Option<&T> { ... }

## Bad

- pub fn at(&self, index: usize) -> &T { ... } // the only accessor, and it panics
