---
type: Styleguide Rule
description: |-
  All unsafe code should be tested with Miri to catch undefined
  behavior. Miri is a Rust interpreter that detects UB.
language: rust
category: practices
rule_id: MIRI-FOR-UNSAFE
priority: error
tags:
- practices
- unsafe
- testing
- carmack
---
All unsafe code should be tested with Miri to catch undefined
behavior. Miri is a Rust interpreter that detects UB.

## Good

- cargo +nightly miri test

## Bad

- # Unsafe code never tested with Miri
