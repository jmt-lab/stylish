---
type: Styleguide Rule
description: |-
  Functions that can panic should document when and why. If a panic
  represents a programmer error, say so.
language: rust
category: comments
rule_id: PANIC-JUSTIFICATION
priority: warn
tags:
- documentation
- panics
- safety
---
Functions that can panic should document when and why. If a panic
represents a programmer error, say so.

## Good

- /// # Panics
/// Panics if index is out of bounds. This is a programmer error;
/// callers must ensure index < len.
fn get_unchecked(&self, index: usize) -> &T

## Bad

- fn get_unchecked(&self, index: usize) -> &T // Can panic, not documented
