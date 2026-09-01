---
type: Styleguide Rule
description: |-
  When you need both index and value, use enumerate. More Pythonic
  and less error-prone.
language: python
category: control_flow
rule_id: ENUMERATE-OVER-RANGE-LEN
priority: warn
tags:
- loops
- enumerate
- pythonic
---
When you need both index and value, use enumerate. More Pythonic
and less error-prone.

## Good

- for i, item in enumerate(items):
    process(i, item)

## Bad

- for i in range(len(items)):
    process(i, items[i])
