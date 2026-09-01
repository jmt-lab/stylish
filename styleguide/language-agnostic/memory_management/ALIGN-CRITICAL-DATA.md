---
type: Styleguide Rule
description: |-
  Allocate SIMD and cache-sensitive data with appropriate alignment.
  Provide aligned allocation variants.
language: language-agnostic
category: memory_management
rule_id: ALIGN-CRITICAL-DATA
priority: warn
tags:
- alignment
- performance
- simd
---
Allocate SIMD and cache-sensitive data with appropriate alignment.
Provide aligned allocation variants.

## Good

- Mem_Alloc16(size); // 16-byte aligned for SSE
- Mem_AllocAligned(size, 64); // Cache line aligned

## Bad

- Mem_Alloc(size); // Wrong alignment for SIMD
