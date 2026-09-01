---
type: Styleguide Rule
description: |-
  Different size classes should use different allocators optimized
  for that size range (small, medium, large).
language: language-agnostic
category: memory_management
rule_id: TIERED-ALLOCATORS
priority: warn
tags:
- allocation
- performance
- optimization
---
Different size classes should use different allocators optimized
for that size range (small, medium, large).

## Good

- // Small: pool allocator
// Medium: block allocator
// Large: direct allocation

## Bad

- // One allocator for everything
