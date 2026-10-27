---
type: Styleguide Rule
description: |-
  Return results as values (a tuple, struct, Option, or Result), not
  through &mut out-parameters. The exception is letting callers reuse a
  buffer they own, as Read::read does.
language: rust
category: api_design
rule_id: RETURN-VALUES-NOT-OUT-PARAMS
priority: warn
tags:
- api-design
- parameters
- return-values
- beautiful-rust
---
Return results as values (a tuple, struct, Option, or Result), not
through &mut out-parameters. The exception is letting callers reuse a
buffer they own, as Read::read does.

## Good

- fn parse_header(line: &str) -> Result<Header, ParseError> { ... }
- fn read_into(&mut self, buf: &mut Vec<u8>) -> io::Result<usize> { ... } // buffer reuse

## Bad

- fn parse_header(line: &str, out: &mut Header, err_line: &mut usize) -> bool { ... }
