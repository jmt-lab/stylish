---
type: Styleguide Rule
description: Dependencies must be alphabetized by crate name in all sections of Cargo.toml files
language: rust
category: cargo
rule_id: CARGO-DEPS-ALPHABETIZE
priority: warn
tags:
- dependencies
- formatting
---
Dependencies must be alphabetized by crate name in all sections of Cargo.toml files

## Good

- [dependencies]
serde = "1.0"
snafu = "0.8"
tokio = "1.0"


## Bad

- [dependencies]
tokio = "1.0"
snafu = "0.8"
serde = "1.0"

