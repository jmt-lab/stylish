---
type: Styleguide Rule
description: |-
  Exceptions are for exceptional conditions, not normal control flow.
  Use explicit conditionals for expected cases.
language: python
category: error_handling
rule_id: NO-EXCEPTION-FLOW
priority: error
tags:
- exceptions
- control-flow
- performance
---
Exceptions are for exceptional conditions, not normal control flow.
Use explicit conditionals for expected cases.

## Good

- if key in cache:
    return cache[key]
return compute(key)

## Bad

- try:
    return cache[key]
except KeyError:
    return compute(key)  # Expected case
