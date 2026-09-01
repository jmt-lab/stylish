---
type: Styleguide Rule
description: |-
  All public functions, methods, and class attributes must have type hints.
  This forms a contract with callers and enables static analysis.
language: python
category: typing
rule_id: TYPE-PUBLIC-API
priority: error
tags:
- api
- contracts
- safety
---
All public functions, methods, and class attributes must have type hints.
This forms a contract with callers and enables static analysis.

## Good

- def get_entity(entity_id: int) -> Entity | None:
- class Config:
    debug: bool
    port: int

## Bad

- def get_entity(entity_id):  # Missing types
- def process(data):  # What type is data?
