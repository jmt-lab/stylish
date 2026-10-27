---
type: Styleguide Rule
description: |-
  Overload operators (Add, Mul, Shl, Index, ...) only for their
  mathematical or logical meaning, never as syntax sugar for unrelated
  operations.
language: rust
category: api_design
rule_id: OPERATOR-OVERLOAD-MATH-ONLY
priority: warn
tags:
- api-design
- operators
- traits
- google-style
---
Overload operators (Add, Mul, Shl, Index, ...) only for their
mathematical or logical meaning, never as syntax sugar for unrelated
operations.

## Good

- impl Add for Vector2 { type Output = Self; fn add(self, rhs: Self) -> Self { ... } }

## Bad

- impl Shl<Message> for Logger { ... }
logger << message; // C++-style stream sugar
- impl Add<Item> for Cart { ... } // cart + item to mean push
