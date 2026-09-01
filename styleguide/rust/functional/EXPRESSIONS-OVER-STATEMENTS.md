---
type: Styleguide Rule
description: |-
  Rust is expression-oriented. Use expressions (if, match, blocks)
  that return values instead of statements with side effects.
language: rust
category: functional
rule_id: EXPRESSIONS-OVER-STATEMENTS
priority: warn
tags:
- functional
- expressions
- immutability
---
Rust is expression-oriented. Use expressions (if, match, blocks)
that return values instead of statements with side effects.

## Good

- let status = if health > 0.0 {
    Status::Alive
} else {
    Status::Dead
};

## Bad

- let mut status;
if health > 0.0 {
    status = Status::Alive;
} else {
    status = Status::Dead;
}
