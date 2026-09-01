---
type: Styleguide Rule
description: |-
  For memory blocks and critical structures, use magic number patterns
  to detect corruption. Assert these in debug builds.
language: language-agnostic
category: error_handling
rule_id: MAGIC-NUMBER-VALIDATION
priority: warn
tags:
- memory
- validation
- debugging
---
For memory blocks and critical structures, use magic number patterns
to detect corruption. Assert these in debug builds.

## Good

- assert(block->magic == 0xDEADBEEF);
- assert(block->id[0] == 0x11111111 && block->id[1] == 0x22222222);

## Bad

- // Just trust the memory is valid
