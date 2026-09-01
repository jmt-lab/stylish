---
type: Styleguide Rule
description: |-
  Prefer explicit for/while loops over clever one-liners when logic
  is non-trivial. Comprehensions are fine for simple transforms.
language: python
category: control_flow
rule_id: EXPLICIT-LOOPS
priority: info
tags:
- loops
- comprehensions
- clarity
---
Prefer explicit for/while loops over clever one-liners when logic
is non-trivial. Comprehensions are fine for simple transforms.

## Good

- for item in items:
    if item.valid:
        process(item)
- valid = [x for x in items if x > 0]  # Simple

## Bad

- [process(x) for x in items if validate(x) and transform(x)]  # Side effects in comprehension
