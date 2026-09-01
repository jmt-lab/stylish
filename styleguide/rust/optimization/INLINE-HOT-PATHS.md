---
type: Styleguide Rule
description: |-
  Small, frequently-called functions should use #[inline] or
  #[inline(always)] when profiling shows benefit.
language: rust
category: optimization
rule_id: INLINE-HOT-PATHS
priority: warn
tags:
- optimization
- inline
- carmack
---
Small, frequently-called functions should use #[inline] or
#[inline(always)] when profiling shows benefit.

## Good

- #[inline]
fn dot(a: Vec3, b: Vec3) -> f32 {
    a.x * b.x + a.y * b.y + a.z * b.z
}

## Bad

- #[inline(always)]
fn load_level() -> Level { ... } // Large, cold function
