---
type: Styleguide Rule
description: |-
  Use dataclasses for structured data instead of dictionaries. They
  provide better type safety and IDE support.
language: python
category: typing
rule_id: DATACLASSES-OVER-DICT
priority: info
tags:
- dataclasses
- structure
- safety
---
Use dataclasses for structured data instead of dictionaries. They
provide better type safety and IDE support.

## Good

- from dataclasses import dataclass
@dataclass
class Entity:
    id: int
    name: str
    health: float

## Bad

- entity = {'id': 1, 'name': 'Player', 'health': 100.0}
