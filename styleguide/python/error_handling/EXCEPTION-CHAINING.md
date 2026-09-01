---
type: Styleguide Rule
description: |-
  When catching and re-raising, use 'raise from' to preserve the original
  exception context. This maintains the full error chain.
language: python
category: error_handling
rule_id: EXCEPTION-CHAINING
priority: error
tags:
- exceptions
- debugging
- context
---
When catching and re-raising, use 'raise from' to preserve the original
exception context. This maintains the full error chain.

## Good

- try:
    parse(data)
except ValueError as e:
    raise ConfigError('Invalid config') from e

## Bad

- try:
    parse(data)
except ValueError:
    raise ConfigError('Invalid config')  # Lost context
