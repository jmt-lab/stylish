---
type: Styleguide Rule
description: |-
  Pytest is the standard. Write tests for all non-trivial code.
  Use fixtures, parametrize, and clear assertions.
language: python
category: practices
rule_id: PYTEST-TESTING
priority: error
tags:
- pytest
- testing
- quality
---
Pytest is the standard. Write tests for all non-trivial code.
Use fixtures, parametrize, and clear assertions.

## Good

- def test_parse_valid():
    assert parse('data') == expected

## Bad

- # No tests or unittest boilerplate
