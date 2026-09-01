---
type: Styleguide Rule
description: |-
  Enable address sanitizer (ASAN) and other sanitizers in CI to
  catch memory errors and undefined behavior.
language: rust
category: practices
rule_id: SANITIZERS-IN-CI
priority: warn
tags:
- practices
- testing
- sanitizers
- carmack
---
Enable address sanitizer (ASAN) and other sanitizers in CI to
catch memory errors and undefined behavior.

## Good

- RUSTFLAGS="-Z sanitizer=address" cargo test

## Bad

- # No sanitizers in CI
