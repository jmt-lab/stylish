---
type: Styleguide Rule
description: |-
  Every dependency costs compile time, binary size, and supply-chain
  exposure (including its build.rs and proc macros). Add one only when it
  pulls its weight, prefer default-features = false, and audit regularly with
  cargo tree --duplicates and cargo udeps.
language: rust
category: practices
rule_id: MINIMIZE-DEPENDENCIES
priority: info
tags:
- practices
- dependencies
- supply-chain
- beautiful-rust
---
Every dependency costs compile time, binary size, and supply-chain
exposure (including its build.rs and proc macros). Add one only when it
pulls its weight, prefer default-features = false, and audit regularly with
cargo tree --duplicates and cargo udeps.

## Good

- [dependencies]
serde = { version = "1", default-features = false, features = ["derive"] }

## Bad

- [dependencies]
left-pad = "1"     # for one 3-line function
tokio = { version = "1", features = ["full"] } # in a library that uses one channel
