---
type: Styleguide Rule
description: |-
  When a function only reads from a list parameter, use Sequence to
  accept any sequence type (list, tuple, etc).
language: python
category: typing
rule_id: SEQUENCE-OVER-LIST
priority: info
tags:
- sequence
- parameters
- flexibility
---
When a function only reads from a list parameter, use Sequence to
accept any sequence type (list, tuple, etc).

## Good

- from collections.abc import Sequence
def sum_values(values: Sequence[int]) -> int:

## Bad

- def sum_values(values: list[int]) -> int:  # Rejects tuples
