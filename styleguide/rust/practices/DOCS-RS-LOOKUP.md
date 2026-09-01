---
type: Styleguide Rule
description: |-
  Look up third-party crate documentation using docs.rs or source code.
  Review crates.io for README, check source repositories for examples,
  understand feature flags and error handling patterns specific to each crate.
language: rust
category: practices
rule_id: DOCS-RS-LOOKUP
priority: warn
tags:
- development
- documentation
- research
---
Look up third-party crate documentation using docs.rs or source code.
Review crates.io for README, check source repositories for examples,
understand feature flags and error handling patterns specific to each crate.

## Good

- # Visit https://docs.rs/serde for API documentation
- # Check GitHub repo for usage examples

## Bad

- # Guess API usage without reading documentation
