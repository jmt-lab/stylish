---
type: Styleguide Rule
description: |-
  Double leading and trailing underscores are reserved for Python magic
  methods. Never invent your own dunder names.
language: python
category: naming
rule_id: DUNDER-METHODS
priority: error
tags:
- magic-methods
- pep8
---
Double leading and trailing underscores are reserved for Python magic
methods. Never invent your own dunder names.

## Good

- def __init__(self):
- def __str__(self):
- def __enter__(self):

## Bad

- def __my_method__(): # Custom dunder
