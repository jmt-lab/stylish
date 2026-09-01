---
type: Styleguide Rule
description: |-
  Objects of the same size allocated frequently should use pool
  allocators for minimal fragmentation and fast allocation.
language: language-agnostic
category: memory_management
rule_id: POOL-ALLOCATORS
priority: info
tags:
- allocation
- performance
- fragmentation
---
Objects of the same size allocated frequently should use pool
allocators for minimal fragmentation and fast allocation.

## Good

- EntityPool* pool = CreatePool(sizeof(Entity), 1024);
entity = PoolAlloc(pool);

## Bad

- entity = malloc(sizeof(Entity)); // General allocator
