---
type: Styleguide Rule
description: |-
  Module-level constants should use uppercase with underscores. This makes
  them immediately distinguishable from variables.
language: python
category: naming
rule_id: SCREAMING-SNAKE-CONSTANTS
priority: error
tags:
- constants
- pep8
---
Module-level constants should use uppercase with underscores. This makes
them immediately distinguishable from variables.

## Good

- MAX_ENTITIES = 1024
- DEFAULT_TIMEOUT = 30
- PI = 3.14159

## Bad

- maxEntities = 1024 # Looks like variable
- Max_Entities = 1024 # Mixed case
