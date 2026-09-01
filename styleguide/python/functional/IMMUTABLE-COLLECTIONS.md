---
type: Styleguide Rule
description: |-
  For data that shouldn't change, use tuple instead of list, frozenset
  instead of set. Makes immutability explicit and enables hashing.
language: python
category: functional
rule_id: IMMUTABLE-COLLECTIONS
priority: info
tags:
- immutability
- collections
- types
---
For data that shouldn't change, use tuple instead of list, frozenset
instead of set. Makes immutability explicit and enables hashing.

## Good

- VALID_STATES: frozenset[str] = frozenset(['active', 'paused', 'stopped'])
- def get_coords() -> tuple[int, int, int]:

## Bad

- VALID_STATES: list[str] = ['active', 'paused', 'stopped']  # Mutable constant
