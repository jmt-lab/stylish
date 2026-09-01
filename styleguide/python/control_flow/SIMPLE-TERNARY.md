---
type: Styleguide Rule
description: |-
  Ternary expressions are fine for simple value selection. Avoid
  complex expressions or nested ternaries.
language: python
category: control_flow
rule_id: SIMPLE-TERNARY
priority: info
tags:
- ternary
- conditionals
- clarity
---
Ternary expressions are fine for simple value selection. Avoid
complex expressions or nested ternaries.

## Good

- result = value if value > 0 else 0

## Bad

- result = a if x > y else (b if z < w else (c if p else d))
