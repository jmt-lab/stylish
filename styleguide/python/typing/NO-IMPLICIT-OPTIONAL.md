---
type: Styleguide Rule
description: |-
  Don't rely on default=None implying Optional. Explicitly type as
  Optional to make nullability clear.
language: python
category: typing
rule_id: NO-IMPLICIT-OPTIONAL
priority: error
tags:
- optional
- explicitness
- clarity
---
Don't rely on default=None implying Optional. Explicitly type as
Optional to make nullability clear.

## Good

- def process(data: str | None = None) -> None:

## Bad

- def process(data: str = None) -> None:  # Implicit Optional
