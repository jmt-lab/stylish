---
type: Styleguide Rule
description: |-
  Every function parameter should have a type hint. This documents
  expectations and prevents type errors.
language: python
category: typing
rule_id: TYPE-PARAMETERS
priority: error
tags:
- parameters
- functions
- clarity
---
Every function parameter should have a type hint. This documents
expectations and prevents type errors.

## Good

- def transform(position: Vector3, scale: float) -> Vector3:

## Bad

- def transform(position, scale):  # Unclear types
