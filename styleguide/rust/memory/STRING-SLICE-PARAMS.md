---
type: Styleguide Rule
description: |-
  Functions that only read strings should accept &str, not &String.
  This works with String, &str, and string literals.
language: rust
category: memory
rule_id: STRING-SLICE-PARAMS
priority: warn
tags:
- memory
- strings
- api-design
---
Functions that only read strings should accept &str, not &String.
This works with String, &str, and string literals.

## Good

- fn load_file(path: &str) -> Result<Data, Error>

## Bad

- fn load_file(path: &String) -> Result<Data, Error> // Too specific
