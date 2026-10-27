---
type: Styleguide Rule
description: |-
  Write hexadecimal literals with lowercase digits (rustfmt setting
  hex_literal_case = "Lower").
language: rust
category: formatting
rule_id: LOWERCASE-HEX-LITERALS
priority: info
tags:
- formatting
- literals
- rustfmt
- google-style
---
Write hexadecimal literals with lowercase digits (rustfmt setting
hex_literal_case = "Lower").

## Good

- const MASK: u32 = 0xdead_beef;
- let color = 0xff00ff;

## Bad

- const MASK: u32 = 0xDEAD_BEEF;
- let color = 0xFf00fF;
