---
type: Styleguide Rule
description: |-
  All class attributes should have type annotations, either in __init__
  or as class-level annotations.
language: python
category: typing
rule_id: TYPE-CLASS-ATTRIBUTES
priority: error
tags:
- classes
- attributes
- clarity
---
All class attributes should have type annotations, either in __init__
or as class-level annotations.

## Good

- class Entity:
    health: float
    name: str
    def __init__(self, name: str):
        self.name = name
        self.health = 100.0

## Bad

- class Entity:
    def __init__(self, name):
        self.name = name  # No types
