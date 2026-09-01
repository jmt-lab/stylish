---
type: Styleguide Rule
description: |-
  Return multiple values as tuples and unpack at call site. More
  Pythonic than output parameters or mutable containers.
language: python
category: functional
rule_id: TUPLE-UNPACKING
priority: info
tags:
- unpacking
- returns
- pythonic
---
Return multiple values as tuples and unpack at call site. More
Pythonic than output parameters or mutable containers.

## Good

- def parse(s: str) -> tuple[bool, int]:
    return True, int(s)

success, value = parse("42")

## Bad

- def parse(s: str, out: dict) -> None:
    out['success'] = True
    out['value'] = int(s)
