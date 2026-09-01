---
type: Styleguide Rule
description: |-
  Better algorithms beat micro-optimizations. O(n²) → O(n log n) is
  more valuable than shaving cycles from inner loop.
language: language-agnostic
category: optimization
rule_id: ALGORITHMIC-FIRST
priority: error
tags:
- algorithms
- complexity
- big-o
---
Better algorithms beat micro-optimizations. O(n²) → O(n log n) is
more valuable than shaving cycles from inner loop.

## Good

- // Use hash table O(1) instead of linear search O(n)

## Bad

- // Micro-optimize the O(n²) loop
