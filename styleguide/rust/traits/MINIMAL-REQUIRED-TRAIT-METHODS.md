---
type: Styleguide Rule
description: |-
  Keep a trait's required methods minimal and provide default
  implementations for everything derivable from them, as Iterator does from
  next(). Adding a defaulted method later is backward compatible.
language: rust
category: traits
rule_id: MINIMAL-REQUIRED-TRAIT-METHODS
priority: info
tags:
- traits
- default-methods
- api-design
- beautiful-rust
---
Keep a trait's required methods minimal and provide default
implementations for everything derivable from them, as Iterator does from
next(). Adding a defaulted method later is backward compatible.

## Good

- pub trait Shape {
    fn area(&self) -> f64;
    fn is_larger_than(&self, other: &dyn Shape) -> bool { self.area() > other.area() }
}

## Bad

- pub trait Shape {
    fn area(&self) -> f64;
    fn is_larger_than(&self, other: &dyn Shape) -> bool; // every impl writes the same code
}
