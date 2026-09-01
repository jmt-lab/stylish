---
type: Styleguide Rule
description: |-
  Per-frame temporary allocations should use fast bump allocators
  that reset entirely each frame. No individual frees needed.
language: language-agnostic
category: memory_management
rule_id: FRAME-ALLOCATORS
priority: warn
tags:
- allocation
- performance
- temporary
---
Per-frame temporary allocations should use fast bump allocators
that reset entirely each frame. No individual frees needed.

## Good

- temp = FrameAlloc(size); // Freed at frame end
- FrameAllocator.Reset(); // O(1) clear

## Bad

- temp = malloc(size);
...
free(temp); // Per-allocation overhead
