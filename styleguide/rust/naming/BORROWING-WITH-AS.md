---
type: Styleguide Rule
description: |-
  Methods that borrow and convert to a different type should use
  'as_' prefix.
language: rust
category: naming
rule_id: BORROWING-WITH-AS
priority: warn
tags:
- naming
- convention
- borrowing
- official
---
Methods that borrow and convert to a different type should use
'as_' prefix.

## Good

- fn as_bytes(&self) -> &[u8]
- fn as_str(&self) -> &str
- fn as_mut_ptr(&mut self) -> *mut T

## Bad

- fn bytes(&self) -> &[u8] // Should be as_bytes
