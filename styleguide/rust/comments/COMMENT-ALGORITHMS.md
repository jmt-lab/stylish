---
type: Styleguide Rule
description: |-
  Complex algorithms or optimizations should be commented with
  explanation and references when applicable.
language: rust
category: comments
rule_id: COMMENT-ALGORITHMS
priority: warn
tags:
- comments
- algorithms
- carmack
---
Complex algorithms or optimizations should be commented with
explanation and references when applicable.

## Good

- // Fast inverse square root (Quake III algorithm)
// See: https://en.wikipedia.org/wiki/Fast_inverse_square_root
let magic = 0x5f3759df - (i >> 1);

## Bad

- // Math stuff
let result = complex_calculation();
