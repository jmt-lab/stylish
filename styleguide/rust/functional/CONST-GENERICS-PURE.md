---
type: Styleguide Rule
description: |-
  Const generics enable type-level programming for pure, zero-cost
  abstractions with compile-time guarantees.
language: rust
category: functional
rule_id: CONST-GENERICS-PURE
priority: info
tags:
- functional
- const-generics
- type-level
---
Const generics enable type-level programming for pure, zero-cost
abstractions with compile-time guarantees.

## Good

- struct Array<T, const N: usize> {
    data: [T; N],
}
impl<T, const N: usize> Array<T, N> {
    fn len(&self) -> usize { N } // Compile-time constant
}

## Bad

- struct Array<T> {
    data: Vec<T>,
    len: usize, // Runtime value
}
