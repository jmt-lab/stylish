---
type: Styleguide Rule
description: |-
  Name constructors new(), or new_with_foo() when there are several. Name
  fallible constructors try_new(). Use from_foo() for value-to-value
  conversions, paired with a matching From impl.
language: rust
category: naming
rule_id: CONSTRUCTOR-NAMING
priority: warn
tags:
- naming
- constructors
- conventions
- google-style
---
Name constructors new(), or new_with_foo() when there are several. Name
fallible constructors try_new(). Use from_foo() for value-to-value
conversions, paired with a matching From impl.

## Good

- impl Buffer {
    pub fn new() -> Self { ... }
    pub fn new_with_capacity(capacity: usize) -> Self { ... }
}
- pub fn try_new(port: u16) -> Result<Self, InvalidPortError> { ... }
- pub fn from_bytes(bytes: [u8; 4]) -> Self { ... } // plus impl From<[u8; 4]>

## Bad

- pub fn create() -> Self { ... }
- pub fn new(port: u16) -> Result<Self, InvalidPortError> { ... } // fallible but named new
- pub fn make_buffer_sized(capacity: usize) -> Self { ... }
