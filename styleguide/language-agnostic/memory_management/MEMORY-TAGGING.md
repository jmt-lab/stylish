---
type: Styleguide Rule
description: |-
  Every allocation should be tagged with its purpose for debugging
  and profiling. Track who allocated what.
language: language-agnostic
category: memory_management
rule_id: MEMORY-TAGGING
priority: warn
tags:
- debugging
- profiling
- tracking
---
Every allocation should be tagged with its purpose for debugging
and profiling. Track who allocated what.

## Good

- Mem_Alloc(size, TAG_MODEL);
- Mem_Alloc(size, TAG_IMAGE);
- Mem_Alloc(size, TAG_ENTITY);

## Bad

- Mem_Alloc(size); // No tag
