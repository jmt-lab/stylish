---
type: Styleguide Rule
description: |-
  Properties that can be checked at compile time should use const
  assertions, not runtime checks.
language: rust
category: error_handling
rule_id: STATIC-ASSERTIONS
priority: info
tags:
- assertions
- compile-time
- static
---
Properties that can be checked at compile time should use const
assertions, not runtime checks.

## Good

- const _: () = assert!(std::mem::size_of::<Entity>() <= 64);
- const _: () = assert!(std::mem::align_of::<Vec3>() == 16);

## Bad

- // Runtime check for static property
assert!(std::mem::size_of::<Entity>() <= 64);
