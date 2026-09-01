---
type: Styleguide Rule
description: |-
  Review core dependencies and their versions in Cargo.toml before
  development. Note enabled feature flags, distinguish between dev/runtime/build
  dependencies, and identify optional dependencies to leverage existing
  functionality and maintain architectural consistency.
language: rust
category: practices
rule_id: SCAN-CARGO-TOML
priority: error
tags:
- development
- dependencies
- workflow
---
Review core dependencies and their versions in Cargo.toml before
development. Note enabled feature flags, distinguish between dev/runtime/build
dependencies, and identify optional dependencies to leverage existing
functionality and maintain architectural consistency.

## Good

- # Review Cargo.toml dependencies section
# Note: using serde with derive feature
# tokio with rt-multi-thread for async runtime

## Bad

- # Start coding without understanding dependency landscape
