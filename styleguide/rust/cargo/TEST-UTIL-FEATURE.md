---
type: Styleguide Rule
description: |-
  Put mocks, fakes, test data generators, and safety overrides behind a
  single test-util feature rather than shipping them in the default API or
  duplicating them across crates' tests.
language: rust
category: cargo
rule_id: TEST-UTIL-FEATURE
priority: info
tags:
- cargo
- features
- testing
- mocks
- beautiful-rust
---
Put mocks, fakes, test data generators, and safety overrides behind a
single test-util feature rather than shipping them in the default API or
duplicating them across crates' tests.

## Good

- [features]
test-util = []

#[cfg(feature = "test-util")]
pub mod mock;

## Bad

- pub mod mock; // MockClient shipped to every production user
