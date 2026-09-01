---
type: Styleguide Rule
description: |-
  Operations that can fail for expected reasons (I/O, parsing, network)
  should return Result<T, E>, not panic.
language: rust
category: error_handling
rule_id: RESULT-FOR-EXPECTED-ERRORS
priority: error
tags:
- errors
- result
- expected-failures
---
Operations that can fail for expected reasons (I/O, parsing, network)
should return Result<T, E>, not panic.

## Good

- fn load_level(path: &Path) -> Result<Level, LoadError>
- fn parse_config(data: &str) -> Result<Config, ParseError>

## Bad

- fn load_level(path: &Path) -> Level // What if file missing?
