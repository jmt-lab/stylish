---
type: Styleguide Rule
description: |-
  SIMD (portable_simd, wide crate) should target profiled hot paths.
  Measure impact; SIMD isn't always faster.
language: rust
category: optimization
rule_id: SIMD-WHEN-MEASURED
priority: warn
tags:
- optimization
- simd
- carmack
---
SIMD (portable_simd, wide crate) should target profiled hot paths.
Measure impact; SIMD isn't always faster.

## Good

- // Profiled: vector math is 25% of time
use std::simd::f32x4;
fn process_batch(data: &[f32x4])

## Bad

- // Let's SIMD everything! (no measurement)
