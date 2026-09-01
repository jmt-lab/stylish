---
type: Styleguide Rule
description: |-
  Check error conditions at function start and return early. Keeps
  happy path at base indentation level.
language: python
category: control_flow
rule_id: EARLY-RETURN
priority: warn
tags:
- returns
- guards
- clarity
---
Check error conditions at function start and return early. Keeps
happy path at base indentation level.

## Good

- def process(entity):
    if entity is None:
        return None
    if not entity.is_valid():
        return None
    # Happy path
    return entity.compute()

## Bad

- def process(entity):
    if entity is not None:
        if entity.is_valid():
            # Happy path nested
            return entity.compute()
    return None
