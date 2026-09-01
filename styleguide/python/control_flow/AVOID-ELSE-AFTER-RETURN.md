---
type: Styleguide Rule
description: |-
  If a block ends with return/raise/break/continue, the else is
  redundant. Remove it to reduce nesting.
language: python
category: control_flow
rule_id: AVOID-ELSE-AFTER-RETURN
priority: info
tags:
- conditionals
- returns
- clarity
---
If a block ends with return/raise/break/continue, the else is
redundant. Remove it to reduce nesting.

## Good

- if error:
    return None
return process()

## Bad

- if error:
    return None
else:
    return process()
