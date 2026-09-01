---
type: Styleguide Rule
description: |-
  Specify element types for containers (list, dict, set). This enables
  type checking of container contents.
language: python
category: typing
rule_id: USE-GENERICS
priority: error
tags:
- generics
- containers
- specificity
---
Specify element types for containers (list, dict, set). This enables
type checking of container contents.

## Good

- def get_ids() -> list[int]:
- cache: dict[str, Entity] = {}

## Bad

- def get_ids() -> list:  # List of what?
- cache: dict = {}  # Keys and values unknown
