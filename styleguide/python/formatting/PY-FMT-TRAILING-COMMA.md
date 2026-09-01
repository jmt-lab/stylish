---
type: Styleguide Rule
description: Use trailing commas in multi-line collections. Reduces diff noise and prevents errors.
language: python
category: formatting
rule_id: PY-FMT-TRAILING-COMMA
priority: info
tags:
- formatting
- maintainability
- diff-friendly
---
Use trailing commas in multi-line collections. Reduces diff noise and prevents errors.

## Good

- items = [
    'first',
    'second',
    'third',
]

- def function(
    arg1,
    arg2,
):
    pass


## Bad

- items = [
    'first',
    'second',
    'third'
]

