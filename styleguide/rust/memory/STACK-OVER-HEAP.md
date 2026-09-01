---
type: Styleguide Rule
description: |-
  When size is known at compile time and reasonable, use stack
  allocation (arrays) instead of heap (Vec).
language: rust
category: memory
rule_id: STACK-OVER-HEAP
priority: info
tags:
- memory
- stack
- performance
---
When size is known at compile time and reasonable, use stack
allocation (arrays) instead of heap (Vec).

## Good

- let buffer = [0u8; 256]; // Stack allocation
- let small_vec = smallvec![1, 2, 3]; // Stack up to threshold

## Bad

- let buffer = vec![0u8; 256]; // Heap allocation for small buffer
