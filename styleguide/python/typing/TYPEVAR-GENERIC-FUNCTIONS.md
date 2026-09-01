---
type: Styleguide Rule
description: |-
  When a function works with any type but preserves type relationships,
  use TypeVar to express this constraint.
language: python
category: typing
rule_id: TYPEVAR-GENERIC-FUNCTIONS
priority: warn
tags:
- typevar
- generics
- polymorphism
---
When a function works with any type but preserves type relationships,
use TypeVar to express this constraint.

## Good

- from typing import TypeVar
T = TypeVar('T')
def first(items: list[T]) -> T | None:

## Bad

- def first(items: list) -> Any:  # Lost type information
