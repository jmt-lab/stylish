---
type: Styleguide Rule
description: |-
  Custom exception classes should end with 'Error' suffix to make their
  purpose immediately clear.
language: python
category: naming
rule_id: EXCEPTION-SUFFIX
priority: warn
tags:
- exceptions
- classes
- clarity
---
Custom exception classes should end with 'Error' suffix to make their
purpose immediately clear.

## Good

- class ValidationError(Exception):
- class NetworkError(Exception):
- class ConfigError(Exception):

## Bad

- class InvalidConfig(Exception): # No Error suffix
- class NetworkFailure(Exception): # Use Error
