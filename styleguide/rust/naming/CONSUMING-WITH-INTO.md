---
type: Styleguide Rule
description: |-
  Methods that consume self and return a different type should use
  'into_' prefix.
language: rust
category: naming
rule_id: CONSUMING-WITH-INTO
priority: warn
tags:
- naming
- convention
- ownership
- official
---
Methods that consume self and return a different type should use
'into_' prefix.

## Good

- fn into_raw(self) -> *mut T
- fn into_inner(self) -> T
- fn into_bytes(self) -> Vec<u8>

## Bad

- fn raw(self) -> *mut T // Should be into_raw
