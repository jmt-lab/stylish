---
type: Styleguide Rule
description: |-
  Name tests with pattern test_<function>_<scenario>_<expected_result>.
  Test names should document behavior, not implementation.
language: rust
category: testing
rule_id: DESCRIPTIVE-TEST-NAMES
priority: warn
tags:
- testing
- naming
- documentation
---
Name tests with pattern test_<function>_<scenario>_<expected_result>.
Test names should document behavior, not implementation.

## Good

- test_parse_valid_json_returns_ok
- test_divide_by_zero_returns_error

## Bad

- test1
- test_basic
- test_parse
