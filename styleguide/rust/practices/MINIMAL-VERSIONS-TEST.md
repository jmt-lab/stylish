---
type: Styleguide Rule
description: |-
  Use cargo-minimal-versions to test with oldest allowed dependency
  versions. Ensures version constraints are correct.
language: rust
category: practices
rule_id: MINIMAL-VERSIONS-TEST
priority: info
tags:
- practices
- dependencies
- testing
---
Use cargo-minimal-versions to test with oldest allowed dependency
versions. Ensures version constraints are correct.

## Good

- cargo +nightly minimal-versions check

## Bad

- # Only test with latest versions
