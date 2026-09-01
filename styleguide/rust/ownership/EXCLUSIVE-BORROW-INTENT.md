---
type: Styleguide Rule
description: |-
  Exclusive borrows (&mut T) should only be used when the function
  actually modifies the data. This makes mutation explicit.
language: rust
category: ownership
rule_id: EXCLUSIVE-BORROW-INTENT
priority: error
tags:
- ownership
- borrowing
- mutation
---
Exclusive borrows (&mut T) should only be used when the function
actually modifies the data. This makes mutation explicit.

## Good

- fn update_position(entity: &mut Entity, delta: Vec3)
- fn apply_damage(health: &mut f32, amount: f32)

## Bad

- fn get_name(entity: &mut Entity) -> &str // Doesn't mutate
