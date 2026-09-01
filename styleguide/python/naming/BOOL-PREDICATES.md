---
type: Styleguide Rule
description: |-
  Boolean functions and variables should use predicate prefixes to make
  their return type obvious. Follows Carmack's clarity principle.
language: python
category: naming
rule_id: BOOL-PREDICATES
priority: warn
tags:
- booleans
- functions
- clarity
---
Boolean functions and variables should use predicate prefixes to make
their return type obvious. Follows Carmack's clarity principle.

## Good

- def is_valid():
- def has_children():
- def can_move():
- is_active = True

## Bad

- def valid(): # Ambiguous
- def children(): # Unclear return type
