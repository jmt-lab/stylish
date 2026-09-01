---
type: Styleguide Rule
description: |-
  Computation that can happen at compile time should use const fn.
  This moves work from runtime to compile time.
language: rust
category: optimization
rule_id: CONST-FN-COMPILE-TIME
priority: info
tags:
- optimization
- const
- compile-time
---
Computation that can happen at compile time should use const fn.
This moves work from runtime to compile time.

## Good

- const fn compute_table_size(max: usize) -> usize {
    max * 2 + 1
}
const TABLE_SIZE: usize = compute_table_size(1024);

## Bad

- fn compute_table_size(max: usize) -> usize {
    max * 2 + 1
}
let table_size = compute_table_size(1024); // Runtime
