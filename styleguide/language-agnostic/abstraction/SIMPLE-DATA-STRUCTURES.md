---
type: Styleguide Rule
description: |-
  Use the simplest data structure that meets needs. Array often beats
  complex tree or graph. Simple is fast, debuggable, and maintainable.
language: language-agnostic
category: abstraction
rule_id: SIMPLE-DATA-STRUCTURES
priority: info
tags:
- data-structures
- simplicity
- performance
---
Use the simplest data structure that meets needs. Array often beats
complex tree or graph. Simple is fast, debuggable, and maintainable.

## Good

- // Simple array, linear search
Entity entities[MAX_ENTITIES];

## Bad

- // Complex structure for 10 items
BalancedTreeMapWithCustomComparator...
