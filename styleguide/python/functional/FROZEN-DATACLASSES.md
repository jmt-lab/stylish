---
type: Styleguide Rule
description: |-
  When defining data structures, use dataclasses with frozen=True to
  prevent mutation. Immutable data prevents entire classes of bugs.
language: python
category: functional
rule_id: FROZEN-DATACLASSES
priority: warn
tags:
- dataclasses
- immutability
- safety
---
When defining data structures, use dataclasses with frozen=True to
prevent mutation. Immutable data prevents entire classes of bugs.

## Good

- @dataclass(frozen=True)
class Config:
    host: str
    port: int

## Bad

- @dataclass
class Config:  # Mutable by default
    host: str
    port: int
