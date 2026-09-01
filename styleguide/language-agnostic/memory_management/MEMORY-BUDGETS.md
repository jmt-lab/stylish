---
type: Styleguide Rule
description: |-
  Each subsystem should have a memory budget. Track usage and warn
  when approaching limits.
language: language-agnostic
category: memory_management
rule_id: MEMORY-BUDGETS
priority: info
tags:
- budgets
- tracking
- constraints
---
Each subsystem should have a memory budget. Track usage and warn
when approaching limits.

## Good

- if (textureMemory > TEXTURE_BUDGET) {
    Warning('Texture budget exceeded');
}

## Bad

- // No tracking of memory usage
