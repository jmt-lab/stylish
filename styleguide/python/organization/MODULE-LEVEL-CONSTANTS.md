---
type: Styleguide Rule
description: |-
  Module-level constants should be at the top after imports,
  in UPPER_CASE. Makes configuration explicit and discoverable.
language: python
category: organization
rule_id: MODULE-LEVEL-CONSTANTS
priority: info
tags:
- constants
- organization
- readability
---
Module-level constants should be at the top after imports,
in UPPER_CASE. Makes configuration explicit and discoverable.

## Good

- import os

MAX_ENTITIES = 1024
DEFAULT_TIMEOUT = 30.0

## Bad

- class Config:
    max_entities = 1024  # Hidden in class
