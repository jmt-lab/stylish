---
type: Styleguide Rule
description: |-
  If type checking must be suppressed with # type: ignore, document why
  this is necessary and safe.
language: python
category: typing
rule_id: TYPE-IGNORE-DOCUMENTED
priority: error
tags:
- type-ignore
- documentation
- safety
---
If type checking must be suppressed with # type: ignore, document why
this is necessary and safe.

## Good

- # type: ignore[attr-defined]  # Dynamic attribute from metaclass

## Bad

- result = func()  # type: ignore  # Why?
