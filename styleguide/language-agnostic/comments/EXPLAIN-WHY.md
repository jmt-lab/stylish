---
type: Styleguide Rule
description: |-
  Comments should explain the reasoning behind code, not describe what
  the code obviously does. Trust the reader to understand basic syntax.
language: language-agnostic
category: comments
rule_id: EXPLAIN-WHY
priority: warn
tags:
- content
- clarity
- intent
---
Comments should explain the reasoning behind code, not describe what
the code obviously does. Trust the reader to understand basic syntax.

## Good

- // Initialize endian conversion before anything else
Swap_Init();
- // Workaround for driver bug on AMD GPUs

## Bad

- // Set x to 5
x = 5;
- // Loop through entities
for (entity in entities)
