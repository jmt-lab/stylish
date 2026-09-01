---
type: Styleguide Rule
description: |-
  When using dictionaries as structured data, define a TypedDict to
  specify required keys and value types.
language: python
category: typing
rule_id: TYPED-DICT
priority: warn
tags:
- typeddict
- dictionaries
- structure
---
When using dictionaries as structured data, define a TypedDict to
specify required keys and value types.

## Good

- from typing import TypedDict
class EntityData(TypedDict):
    id: int
    name: str
    health: float

## Bad

- def process(data: dict) -> None:  # What keys exist?
