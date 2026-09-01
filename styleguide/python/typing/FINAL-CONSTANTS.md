---
type: Styleguide Rule
description: |-
  Mark module-level and class-level constants with Final to prevent
  reassignment. This is Python's const for values.
language: python
category: typing
rule_id: FINAL-CONSTANTS
priority: error
tags:
- constants
- immutability
- final
---
Mark module-level and class-level constants with Final to prevent
reassignment. This is Python's const for values.

## Good

- from typing import Final
MAX_ENTITIES: Final = 1024
- class Config:
    DEBUG: Final[bool] = False

## Bad

- MAX_ENTITIES = 1024  # Can be reassigned
