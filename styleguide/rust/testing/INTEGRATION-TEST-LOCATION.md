---
type: Styleguide Rule
description: |-
  Integration tests go in tests/ at crate root. Unit tests use
  #[cfg(test)] modules. Each file in tests/ is a separate crate.
language: rust
category: testing
rule_id: INTEGRATION-TEST-LOCATION
priority: warn
tags:
- testing
- organization
- official
---
Integration tests go in tests/ at crate root. Unit tests use
#[cfg(test)] modules. Each file in tests/ is a separate crate.

## Good

- tests/integration_test.rs
- tests/common/mod.rs  // shared utilities

## Bad

- src/integration_tests.rs
