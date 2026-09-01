---
type: Styleguide Rule
description: Dependencies used across multiple crates should be included in the workspace dependencies section
language: rust
category: cargo
rule_id: CARGO-WORKSPACE-COMMON
priority: warn
tags:
- workspace
- dependencies
---
Dependencies used across multiple crates should be included in the workspace dependencies section

## Good

- [workspace.dependencies]
serde = "1.0"
tokio = "1.0"

# In member crate:
[dependencies]
serde.workspace = true


## Bad

- # crate1/Cargo.toml
[dependencies]
serde = "1.0"

# crate2/Cargo.toml
[dependencies]
serde = "1.0"

