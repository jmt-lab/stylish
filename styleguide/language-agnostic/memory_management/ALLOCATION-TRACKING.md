---
type: Styleguide Rule
description: |-
  Debug builds should track file and line number of every allocation
  for leak detection and debugging.
language: language-agnostic
category: memory_management
rule_id: ALLOCATION-TRACKING
priority: warn
tags:
- debugging
- tracking
- leaks
---
Debug builds should track file and line number of every allocation
for leak detection and debugging.

## Good

- Mem_Alloc_Debug(size, __FILE__, __LINE__);
- #define Mem_Alloc(s) Mem_Alloc_Debug(s, __FILE__, __LINE__)

## Bad

- // No tracking of allocation source
