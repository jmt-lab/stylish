---
type: Styleguide Rule
description: |-
  Document what exceptions a function raises in docstring. Make error
  conditions part of the function contract.
language: python
category: error_handling
rule_id: EXPLICIT-ERROR-RETURNS
priority: warn
tags:
- documentation
- contracts
- clarity
---
Document what exceptions a function raises in docstring. Make error
conditions part of the function contract.

## Good

- def find_entity(id: int) -> Entity:
    """Find entity by ID.
    
    Raises:
        EntityNotFoundError: If entity doesn't exist.
    """

## Bad

- def find_entity(id):
    # What exceptions can this raise?
