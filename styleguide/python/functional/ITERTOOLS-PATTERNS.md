---
type: Styleguide Rule
description: |-
  For complex iteration patterns, use itertools instead of manual loops.
  More declarative and often more efficient.
language: python
category: functional
rule_id: ITERTOOLS-PATTERNS
priority: info
tags:
- itertools
- iteration
- stdlib
---
For complex iteration patterns, use itertools instead of manual loops.
More declarative and often more efficient.

## Good

- from itertools import chain, groupby
all_items = chain(list1, list2, list3)
grouped = groupby(sorted(items), key=lambda x: x.category)

## Bad

- all_items = []
for lst in [list1, list2, list3]:
    all_items.extend(lst)
