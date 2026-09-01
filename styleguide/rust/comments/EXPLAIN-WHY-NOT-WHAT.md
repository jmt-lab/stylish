---
type: Styleguide Rule
description: |-
  Carmack principle: Comments should explain reasoning, not describe
  what the code obviously does. Trust the reader to understand syntax.
language: rust
category: comments
rule_id: EXPLAIN-WHY-NOT-WHAT
priority: warn
tags:
- comments
- content
- carmack
---
Carmack principle: Comments should explain reasoning, not describe
what the code obviously does. Trust the reader to understand syntax.

## Good

- // Initialize endian conversion before any string operations
Swap::init();
- // Workaround for driver bug on NVIDIA 4xx series
if needs_workaround { ... }

## Bad

- // Set x to 5
x = 5;
- // Loop through entities
for entity in entities { ... }
