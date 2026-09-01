---
type: Styleguide Rule
description: |-
  Every function should declare its return type. Use None for procedures
  that don't return a value.
language: python
category: typing
rule_id: TYPE-RETURN-VALUES
priority: error
tags:
- return-values
- functions
- clarity
---
Every function should declare its return type. Use None for procedures
that don't return a value.

## Good

- def calculate() -> float:
- def log_message(msg: str) -> None:

## Bad

- def calculate():  # What does it return?
