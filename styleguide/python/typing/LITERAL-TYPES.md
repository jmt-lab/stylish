---
type: Styleguide Rule
description: |-
  When a parameter accepts only specific string or int values, use
  Literal to constrain the type.
language: python
category: typing
rule_id: LITERAL-TYPES
priority: warn
tags:
- literal
- constraints
- enums
---
When a parameter accepts only specific string or int values, use
Literal to constrain the type.

## Good

- from typing import Literal
def set_mode(mode: Literal['debug', 'release', 'profile']) -> None:

## Bad

- def set_mode(mode: str) -> None:  # Any string accepted
