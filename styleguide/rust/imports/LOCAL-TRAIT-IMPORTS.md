---
type: Styleguide Rule
description: |-
  Import traits inside the function body that uses them, unless the
  trait's methods are used extensively throughout the file. This keeps the
  trait's effect on method resolution visible where it matters.
language: rust
category: imports
rule_id: LOCAL-TRAIT-IMPORTS
priority: info
tags:
- imports
- traits
- scope
- google-style
---
Import traits inside the function body that uses them, unless the
trait's methods are used extensively throughout the file. This keeps the
trait's effect on method resolution visible where it matters.

## Good

- fn parse_byte(s: &str) -> Result<u8, std::num::ParseIntError> {
    use std::str::FromStr;

    u8::from_str(s)
}

## Bad

- use std::str::FromStr; // imported at module scope for a single call site

fn parse_byte(s: &str) -> Result<u8, std::num::ParseIntError> {
    u8::from_str(s)
}
