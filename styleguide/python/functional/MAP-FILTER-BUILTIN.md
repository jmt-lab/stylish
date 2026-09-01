---
type: Styleguide Rule
description: |-
  Python's comprehensions are more readable than map/filter for simple
  cases. Use map/filter only when passing existing functions without lambda.
language: python
category: functional
rule_id: MAP-FILTER-BUILTIN
priority: info
tags:
- comprehensions
- readability
- pythonic
---
Python's comprehensions are more readable than map/filter for simple
cases. Use map/filter only when passing existing functions without lambda.

## Good

- active = [e for e in entities if e.is_active]
- names = map(str.lower, raw_names)  # Existing function

## Bad

- active = list(filter(lambda e: e.is_active, entities))  # Use comprehension
