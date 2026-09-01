---
type: Styleguide Rule
description: |-
  Never use mutable objects (list, dict) as default arguments. They're
  shared across calls, causing subtle bugs. Use None and create inside.
language: python
category: functional
rule_id: IMMUTABLE-DEFAULTS
priority: error
tags:
- defaults
- mutability
- bugs
---
Never use mutable objects (list, dict) as default arguments. They're
shared across calls, causing subtle bugs. Use None and create inside.

## Good

- def process(items: list[str] | None = None) -> list[str]:
    items = items or []
    return [i.upper() for i in items]

## Bad

- def process(items: list[str] = []) -> list[str]:  # Shared mutable default
