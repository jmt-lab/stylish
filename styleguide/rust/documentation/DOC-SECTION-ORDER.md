---
type: Styleguide Rule
description: |-
  Structure item docs as: one-line summary, extended description, then the
  applicable sections in order: # Examples, # Panics, # Safety. Describe
  parameters in prose, not a table.
language: rust
category: documentation
rule_id: DOC-SECTION-ORDER
priority: info
tags:
- documentation
- rustdoc
- structure
- beautiful-rust
---
Structure item docs as: one-line summary, extended description, then the
applicable sections in order: # Examples, # Panics, # Safety. Describe
parameters in prose, not a table.

## Good

- /// Splits `input` into fixed-size chunks.
///
/// The final chunk may be shorter than `size`.
///
/// # Examples
/// ...
///
/// # Panics
///
/// Panics if `size` is zero.

## Bad

- /// # Panics
/// Panics if size is zero.
/// | param | meaning |
/// |-------|---------|
/// | input | the input |
/// Splits input.
