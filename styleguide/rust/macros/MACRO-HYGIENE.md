---
type: Styleguide Rule
description: |-
  In macro_rules!, bind expression arguments once with let to avoid
  re-evaluating them, accept attributes (#[cfg], #[derive], docs) on items
  the macro emits, keep emitted items private unless the input says pub, and
  make item macros work at both module and function scope.
language: rust
category: macros
rule_id: MACRO-HYGIENE
priority: info
tags:
- macros
- macro-rules
- correctness
- beautiful-rust
---
In macro_rules!, bind expression arguments once with let to avoid
re-evaluating them, accept attributes (#[cfg], #[derive], docs) on items
the macro emits, keep emitted items private unless the input says pub, and
make item macros work at both module and function scope.

## Good

- macro_rules! square {
    ($e:expr) => {{ let value = $e; value * value }};
}

## Bad

- macro_rules! square {
    ($e:expr) => { $e * $e }; // square!(next()) calls next() twice
}
