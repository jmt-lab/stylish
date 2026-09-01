---
type: Styleguide Rule
description: |-
  For Python 3.10+, prefer match statements over long if-elif chains
  when checking a value against multiple patterns.
language: python
category: control_flow
rule_id: MATCH-OVER-IF-CHAINS
priority: info
tags:
- match
- conditionals
- python310
---
For Python 3.10+, prefer match statements over long if-elif chains
when checking a value against multiple patterns.

## Good

- match status:
    case 'active':
        activate()
    case 'paused':
        pause()
    case _:
        error()

## Bad

- if status == 'active':
    activate()
elif status == 'paused':
    pause()
else:
    error()
