---
type: Styleguide Rule
description: |-
  When processing large sequences or when immediate materialization isn't
  needed, use generator expressions. They're memory-efficient and lazy.
language: python
category: functional
rule_id: GENERATOR-EXPRESSIONS
priority: info
tags:
- generators
- memory
- lazy-evaluation
---
When processing large sequences or when immediate materialization isn't
needed, use generator expressions. They're memory-efficient and lazy.

## Good

- total = sum(x**2 for x in large_list)
- first_match = next(e for e in entities if e.id == target)

## Bad

- total = sum([x**2 for x in large_list])  # Materializes list
