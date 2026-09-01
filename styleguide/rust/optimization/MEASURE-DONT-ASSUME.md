---
type: Styleguide Rule
description: |-
  Carmack principle: Modern CPUs are complex. What seems faster may
  be slower. Always measure with real data and hardware.
language: rust
category: optimization
rule_id: MEASURE-DONT-ASSUME
priority: error
tags:
- optimization
- profiling
- measurement
- carmack
---
Carmack principle: Modern CPUs are complex. What seems faster may
be slower. Always measure with real data and hardware.

## Good

- // Benchmarked both approaches
// HashMap: 150ns/lookup
// Vec linear: 80ns/lookup (small n)
let cache: Vec<(Key, Value)> = Vec::new();

## Bad

- // HashMap is O(1), must be faster
let cache: HashMap<Key, Value> = HashMap::new();
