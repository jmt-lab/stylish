---
type: Styleguide Rule
description: |-
  Every unsafe fn and unsafe trait must document, in a # Safety section,
  the invariants callers or implementors must uphold.
language: rust
category: documentation
rule_id: DOCUMENT-UNSAFE-CONTRACTS
priority: error
tags:
- documentation
- unsafe
- safety
- google-style
---
Every unsafe fn and unsafe trait must document, in a # Safety section,
the invariants callers or implementors must uphold.

## Good

- /// Returns the element at `index` without bounds checking.
///
/// # Safety
///
/// `index` must be less than `self.len()`.
pub unsafe fn get_unchecked(&self, index: usize) -> &T { ... }

## Bad

- /// Returns the element at `index`.
pub unsafe fn get_unchecked(&self, index: usize) -> &T { ... }
