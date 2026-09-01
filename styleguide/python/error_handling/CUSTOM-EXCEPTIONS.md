---
type: Styleguide Rule
description: |-
  Create domain-specific exception classes for application errors.
  Inherit from appropriate built-in exceptions.
language: python
category: error_handling
rule_id: CUSTOM-EXCEPTIONS
priority: warn
tags:
- exceptions
- domain-modeling
- clarity
---
Create domain-specific exception classes for application errors.
Inherit from appropriate built-in exceptions.

## Good

- class ConfigError(ValueError):
    pass
- class EntityNotFoundError(LookupError):
    pass

## Bad

- raise Exception('Config invalid')  # Generic
