---
type: Styleguide Rule
description: |-
  Functions that don't need state shouldn't maintain it. Stateless
  operations are easier to test and parallelize.
language: rust
category: functional
rule_id: STATELESS-FUNCTIONS
priority: info
tags:
- functional
- stateless
- carmack
---
Functions that don't need state shouldn't maintain it. Stateless
operations are easier to test and parallelize.

## Good

- fn distance(a: Vec3, b: Vec3) -> f32 { ... }

## Bad

- struct DistanceCalc {
    last_a: Vec3,
    last_b: Vec3,
}
impl DistanceCalc {
    fn calc(&mut self, a: Vec3, b: Vec3) -> f32 { ... }
}
