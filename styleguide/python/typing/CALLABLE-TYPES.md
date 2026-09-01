---
type: Styleguide Rule
description: |-
  When passing functions as parameters, use Callable to specify the
  function signature.
language: python
category: typing
rule_id: CALLABLE-TYPES
priority: warn
tags:
- callable
- functions
- higher-order
---
When passing functions as parameters, use Callable to specify the
function signature.

## Good

- from collections.abc import Callable
def apply(func: Callable[[int], str], value: int) -> str:

## Bad

- def apply(func, value):  # What does func accept?
