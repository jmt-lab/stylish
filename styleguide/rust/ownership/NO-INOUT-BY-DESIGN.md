---
type: Styleguide Rule
description: |-
  Carmack's 'no in-out parameters' rule is enforced by ownership.
  Parameters are either borrowed (&T, &mut T) or owned (T).
language: rust
category: ownership
rule_id: NO-INOUT-BY-DESIGN
priority: info
tags:
- ownership
- parameters
- carmack
- design
---
Carmack's 'no in-out parameters' rule is enforced by ownership.
Parameters are either borrowed (&T, &mut T) or owned (T).

## Good

- fn transform(input: Vec3) -> Vec3 // Takes and returns ownership
- fn update(state: &mut GameState) // Clearly mutable

## Bad

- // C++ in-out pattern doesn't exist in Rust
// fn transform(inout: &mut Vec3) // Clear if reading or writing
