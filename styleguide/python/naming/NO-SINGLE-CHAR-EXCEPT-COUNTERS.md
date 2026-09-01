---
type: Styleguide Rule
description: |-
  Single-character variable names are acceptable only for loop counters
  (i, j, k) or well-known mathematical variables (x, y, z).
language: python
category: naming
rule_id: NO-SINGLE-CHAR-EXCEPT-COUNTERS
priority: info
tags:
- variables
- clarity
---
Single-character variable names are acceptable only for loop counters
(i, j, k) or well-known mathematical variables (x, y, z).

## Good

- for i in range(len(items)):
- x, y, z = position

## Bad

- e = get_entity() # Unclear
- s = calculate() # What is s?
