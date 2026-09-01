---
type: Styleguide Rule
description: |-
  Use cargo-deny to check for security vulnerabilities, license
  issues, and unmaintained dependencies.
language: rust
category: practices
rule_id: CARGO-DENY
priority: warn
tags:
- practices
- security
- dependencies
---
Use cargo-deny to check for security vulnerabilities, license
issues, and unmaintained dependencies.

## Good

- cargo deny check

## Bad

- # No dependency auditing
