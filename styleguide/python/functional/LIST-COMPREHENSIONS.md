---
type: Styleguide Rule
description: |-
  Prefer list comprehensions for transforming sequences. They're more
  declarative, often faster, and make intent clear. Avoid when logic
  becomes complex (>2 clauses).
language: python
category: functional
rule_id: LIST-COMPREHENSIONS
priority: warn
tags:
- comprehensions
- declarative
- readability
---
Prefer list comprehensions for transforming sequences. They're more
declarative, often faster, and make intent clear. Avoid when logic
becomes complex (>2 clauses).

## Good

- active = [e for e in entities if e.is_active]
- squares = [x**2 for x in range(10)]

## Bad

- active = []
for e in entities:
    if e.is_active:
        active.append(e)
