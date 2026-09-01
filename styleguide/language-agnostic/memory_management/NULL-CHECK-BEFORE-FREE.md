---
type: Styleguide Rule
description: |-
  Either check for NULL before calling free, or make your free
  function handle NULL gracefully (like standard free).
language: language-agnostic
category: memory_management
rule_id: NULL-CHECK-BEFORE-FREE
priority: info
tags:
- safety
- defensive
- 'null'
---
Either check for NULL before calling free, or make your free
function handle NULL gracefully (like standard free).

## Good

- if (ptr != NULL) { Free(ptr); }
- // Or: Free(ptr); // Free handles NULL

## Bad

- Free(ptr); // Crashes if NULL
