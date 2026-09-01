---
type: Styleguide Rule
description: |-
  Never use system malloc/free directly for game allocations. Use
  custom allocators appropriate for allocation patterns and lifetimes.
language: language-agnostic
category: memory_management
rule_id: CUSTOM-ALLOCATORS
priority: error
tags:
- allocation
- performance
- tracking
---
Never use system malloc/free directly for game allocations. Use
custom allocators appropriate for allocation patterns and lifetimes.

## Good

- entity = Mem_Alloc(sizeof(Entity), TAG_ENTITY);
- temp = FrameAlloc(size); // Per-frame allocator

## Bad

- entity = malloc(sizeof(Entity)); // System allocator
