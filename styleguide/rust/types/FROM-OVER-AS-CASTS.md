---
type: Styleguide Rule
description: |-
  Convert numbers with From / TryFrom (or into / try_into) instead of as,
  which silently truncates, wraps, or loses sign. Reserve as for cases where
  exact cast semantics are the point (e.g. FFI, bit manipulation), and say so
  (Clippy: as_conversions, cast_possible_truncation, cast_sign_loss).
language: rust
category: types
rule_id: FROM-OVER-AS-CASTS
priority: warn
tags:
- types
- conversions
- casts
- clippy
- beautiful-rust
---
Convert numbers with From / TryFrom (or into / try_into) instead of as,
which silently truncates, wraps, or loses sign. Reserve as for cases where
exact cast semantics are the point (e.g. FFI, bit manipulation), and say so
(Clippy: as_conversions, cast_possible_truncation, cast_sign_loss).

## Good

- let total: u64 = u64::from(count);
- let index = usize::try_from(offset).context(NegativeOffsetSnafu { offset })?;

## Bad

- let total = count as u64;
- let index = offset as usize; // negative offset becomes a huge index
