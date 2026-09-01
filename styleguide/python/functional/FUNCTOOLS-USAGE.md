---
type: Styleguide Rule
description: |-
  Leverage functools.reduce for aggregation, functools.partial for partial
  application, and lru_cache for memoization of pure functions.
language: python
category: functional
rule_id: FUNCTOOLS-USAGE
priority: info
tags:
- functools
- patterns
- stdlib
---
Leverage functools.reduce for aggregation, functools.partial for partial
application, and lru_cache for memoization of pure functions.

## Good

- from functools import reduce
total = reduce(lambda acc, x: acc + x.value, items, 0)
- @lru_cache(maxsize=128)
def expensive_pure_function(n: int) -> int:

## Bad

- total = 0
for item in items:
    total += item.value  # Use reduce
