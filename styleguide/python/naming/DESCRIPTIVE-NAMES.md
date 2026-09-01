---
type: Styleguide Rule
description: |-
  Variable and function names should be descriptive and self-documenting.
  Clarity trumps brevity. Avoid single-letter names except for counters.
language: python
category: naming
rule_id: DESCRIPTIVE-NAMES
priority: warn
tags:
- variables
- readability
- clarity
---
Variable and function names should be descriptive and self-documenting.
Clarity trumps brevity. Avoid single-letter names except for counters.

## Good

- entity_count
- frame_number
- current_position
- for i in range(10): # Counter exception

## Bad

- ent_cnt # Over-abbreviated
- n # Unclear
- tmp # Lazy
