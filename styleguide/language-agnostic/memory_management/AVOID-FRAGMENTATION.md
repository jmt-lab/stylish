---
type: Styleguide Rule
description: |-
  Allocate long-lived objects separately from short-lived. Use
  appropriate allocators for lifetime patterns.
language: language-agnostic
category: memory_management
rule_id: AVOID-FRAGMENTATION
priority: warn
tags:
- fragmentation
- lifetime
- performance
---
Allocate long-lived objects separately from short-lived. Use
appropriate allocators for lifetime patterns.

## Good

- // Persistent data: permanent allocator
// Per-level: level allocator
// Per-frame: frame allocator

## Bad

- // Everything mixed in one heap
