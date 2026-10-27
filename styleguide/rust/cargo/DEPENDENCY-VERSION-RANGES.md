---
type: Styleguide Rule
description: |-
  Specify dependencies with caret ranges ("1", "1.4", "1.4.23"). Never
  use "*", and avoid exact "=" pins except for lockstep companion crates
  such as proc-macro pairs.
language: rust
category: cargo
rule_id: DEPENDENCY-VERSION-RANGES
priority: warn
tags:
- cargo
- dependencies
- semver
- beautiful-rust
---
Specify dependencies with caret ranges ("1", "1.4", "1.4.23"). Never
use "*", and avoid exact "=" pins except for lockstep companion crates
such as proc-macro pairs.

## Good

- [dependencies]
serde = "1"
regex = "1.10"
foo-macros = "=0.4.2" # published in lockstep with foo

## Bad

- [dependencies]
serde = "*"
regex = "=1.10.3"  # blocks every downstream patch upgrade
