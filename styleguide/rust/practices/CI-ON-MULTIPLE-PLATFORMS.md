---
type: Styleguide Rule
description: |-
  CI should test on Linux, macOS, and Windows. Platform-specific
  bugs are common.
language: rust
category: practices
rule_id: CI-ON-MULTIPLE-PLATFORMS
priority: warn
tags:
- practices
- ci
- portability
---
CI should test on Linux, macOS, and Windows. Platform-specific
bugs are common.

## Good

- matrix:
  os: [ubuntu-latest, macos-latest, windows-latest]

## Bad

- # Only test on Linux
