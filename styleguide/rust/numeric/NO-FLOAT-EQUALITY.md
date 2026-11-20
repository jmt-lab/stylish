---
type: Styleguide Rule
description: |-
  Don't compare computed floats with == or !=. Compare against a tolerance
  suited to the magnitude, sort and order with f64::total_cmp, and handle
  NaN explicitly (Clippy: float_cmp).
language: rust
category: numeric
rule_id: NO-FLOAT-EQUALITY
priority: warn
tags:
- numeric
- floats
- correctness
- rust-skills
---
Don't compare computed floats with == or !=. Compare against a tolerance
suited to the magnitude, sort and order with f64::total_cmp, and handle
NaN explicitly (Clippy: float_cmp).

## Good

- /// Measurements are rounded to micrometres upstream.
const TOLERANCE: f64 = 1e-6;

if (measured - expected).abs() <= TOLERANCE { accept(); }

- readings.sort_by(f64::total_cmp);

## Bad

- if 0.1 + 0.2 == 0.3 { accept(); } // false

- readings.sort_by(|a, b| a.partial_cmp(b).unwrap()); // panics on NaN
