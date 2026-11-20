---
type: Styleguide Rule
description: |-
  Implement TryFrom for conversions that can fail instead of ad-hoc from_x
  or parse_x functions that return Result or Option. Callers then get
  try_into() and generic TryFrom bounds for free.
language: rust
category: traits
rule_id: TRYFROM-FOR-FALLIBLE-CONVERSIONS
priority: warn
tags:
- traits
- conversions
- std-traits
- rust-skills
---
Implement TryFrom for conversions that can fail instead of ad-hoc from_x
or parse_x functions that return Result or Option. Callers then get
try_into() and generic TryFrom bounds for free.

## Good

- impl TryFrom<u8> for Opcode {
    type Error = UnknownOpcodeError;

    fn try_from(byte: u8) -> Result<Self, Self::Error> { /* ... */ }
}

## Bad

- impl Opcode {
    pub fn from_byte(byte: u8) -> Option<Self> { /* ... */ }
}
