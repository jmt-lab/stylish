---
type: Styleguide Rule
description: |-
  Run mypy with --strict flag on all code. Type checking is mandatory,
  not optional — treat mypy errors as build failures. Enable strict mode
  or equivalent flags: require type hints for all functions, disallow
  untyped calls and definitions, and enable warn_return_any. This enforces
  comprehensive type checking and catches bugs that dynamic typing hides.
language: python
category: typing
rule_id: MYPY-STRICT
priority: error
tags:
- mypy
- static-analysis
- tooling
- type-checking
- mandatory
- strictness
- configuration
---
Run mypy with --strict flag on all code. Type checking is mandatory,
not optional — treat mypy errors as build failures. Enable strict mode
or equivalent flags: require type hints for all functions, disallow
untyped calls and definitions, and enable warn_return_any. This enforces
comprehensive type checking and catches bugs that dynamic typing hides.

## Good

- # mypy.ini
[mypy]
strict = True
- [mypy]
strict = true
warn_return_any = true
- # mypy --strict src/
# 0 errors

## Bad

- # No mypy configuration or lenient settings
- [mypy]
# Minimal checks only
- # No type checking
# Runtime type errors
