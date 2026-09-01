---
type: Styleguide Rule
description: |-
  Structure data for how it's accessed. Keep hot data together,
  use Structure of Arrays when iterating one field, pad to cache lines.
language: language-agnostic
category: optimization
rule_id: DATA-ORIENTED-LAYOUT
priority: warn
tags:
- cache
- dod
- memory-layout
---
Structure data for how it's accessed. Keep hot data together,
use Structure of Arrays when iterating one field, pad to cache lines.

## Good

- // All positions contiguous for iteration
float positions[N * 3];

## Bad

- // Scattered: position[i], skip, position[i+1], skip...
struct Entity { pos; other[100]; };
