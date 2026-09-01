---
type: Styleguide Rule
description: |-
  Use shared borrows (&T) for read-only access. This is Rust's
  enforcement of Carmack's const parameters.
language: rust
category: ownership
rule_id: SHARED-BORROW-DEFAULT
priority: error
tags:
- ownership
- borrowing
- carmack
---
Use shared borrows (&T) for read-only access. This is Rust's
enforcement of Carmack's const parameters.

## Good

- fn process_entity(entity: &Entity, config: &Config)
- fn distance(a: &Vec3, b: &Vec3) -> f32

## Bad

- fn process_entity(entity: &mut Entity) // Doesn't need mut
