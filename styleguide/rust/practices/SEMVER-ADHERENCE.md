---
type: Styleguide Rule
description: |-
  Version numbers should follow semver: major.minor.patch.
  Breaking changes increment major version.
language: rust
category: practices
rule_id: SEMVER-ADHERENCE
priority: error
tags:
- practices
- versioning
- semver
---
Version numbers should follow semver: major.minor.patch.
Breaking changes increment major version.

## Good

- 0.1.0 -> 0.2.0 (new features)
1.0.0 -> 2.0.0 (breaking changes)

## Bad

- 1.0.0 -> 1.1.0 (but has breaking changes)
