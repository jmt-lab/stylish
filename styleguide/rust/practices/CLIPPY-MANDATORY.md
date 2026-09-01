---
type: Styleguide Rule
description: |-
  Carmack: 'It is irresponsible not to use static analysis.' Run
  clippy and fix all warnings. Use clippy::pedantic for stricter checks.
language: rust
category: practices
rule_id: CLIPPY-MANDATORY
priority: error
tags:
- practices
- static-analysis
- carmack
---
Carmack: 'It is irresponsible not to use static analysis.' Run
clippy and fix all warnings. Use clippy::pedantic for stricter checks.

## Good

- cargo clippy --all-targets --all-features -- -D warnings

## Bad

- # Never run clippy
