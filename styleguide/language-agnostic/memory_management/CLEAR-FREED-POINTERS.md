---
type: Styleguide Rule
description: |-
  Set pointers to NULL after freeing to prevent use-after-free bugs
  and double-free errors.
language: language-agnostic
category: memory_management
rule_id: CLEAR-FREED-POINTERS
priority: warn
tags:
- safety
- use-after-free
- double-free
---
Set pointers to NULL after freeing to prevent use-after-free bugs
and double-free errors.

## Good

- Free(ptr);
ptr = NULL;
- #define SAFE_FREE(p) do { Free(p); (p) = NULL; } while(0)

## Bad

- Free(ptr); // Dangling pointer
