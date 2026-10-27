---
type: Styleguide Rule
description: |-
  Mark a function or trait unsafe only when misuse can cause undefined
  behavior, not because it is dangerous or destructive. delete_database()
  is a safe function.
language: rust
category: safety
rule_id: UNSAFE-MEANS-UB
priority: warn
tags:
- safety
- unsafe
- api-design
- beautiful-rust
---
Mark a function or trait unsafe only when misuse can cause undefined
behavior, not because it is dangerous or destructive. delete_database()
is a safe function.

## Good

- pub fn delete_all(&mut self) -> Result<(), DbError> { ... }
- pub unsafe fn from_raw_parts(ptr: *mut T, len: usize) -> Self { ... }

## Bad

- pub unsafe fn delete_all(&mut self) -> Result<(), DbError> { ... } // dangerous, not UB
