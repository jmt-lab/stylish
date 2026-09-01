---
type: Styleguide Rule
description: Prefer the builder pattern or Default trait when creating structs with 4 or more fields or configuration options. Use the bon crate for builder implementations.
language: rust
category: constructs
rule_id: PREFER-BUILDER-PATTERN
priority: warn
tags:
- builders
- structs
- patterns
---
Prefer the builder pattern or Default trait when creating structs with 4 or more fields or configuration options. Use the bon crate for builder implementations.

## Good

- #[derive(bon::Builder)]
struct Config {
    host: String,
    port: u16,
    timeout: Duration,
}
- #[derive(Default)]
struct Options {
    verbose: bool,
    debug: bool,
}
