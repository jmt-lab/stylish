---
type: Styleguide Rule
description: |-
  Use Optional[T] (or T | None in Python 3.10+) for values that may be
  None. This makes nullability explicit.
language: python
category: typing
rule_id: OPTIONAL-VS-UNION
priority: error
tags:
- nullability
- safety
- optional
---
Use Optional[T] (or T | None in Python 3.10+) for values that may be
None. This makes nullability explicit.

## Good

- def find_entity(id: int) -> Entity | None:
- from typing import Optional
def find(id: int) -> Optional[Entity]:

## Bad

- def find_entity(id: int) -> Entity:  # Can return None!
