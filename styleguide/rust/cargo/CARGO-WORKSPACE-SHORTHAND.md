---
type: Styleguide Rule
description: Use the shorthand .workspace = true syntax for dependencies without special features or configuration
language: rust
category: cargo
rule_id: CARGO-WORKSPACE-SHORTHAND
priority: warn
tags:
- workspace
- dependencies
- syntax
---
Use the shorthand .workspace = true syntax for dependencies without special features or configuration

## Good

- [dependencies]
serde.workspace = true


## Bad

- [dependencies]
serde = { workspace = true }

