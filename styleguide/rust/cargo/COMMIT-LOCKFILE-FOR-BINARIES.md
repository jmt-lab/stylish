---
type: Styleguide Rule
description: |-
  Commit Cargo.lock for binaries and other deployable artifacts so builds
  are reproducible.
language: rust
category: cargo
rule_id: COMMIT-LOCKFILE-FOR-BINARIES
priority: warn
tags:
- cargo
- dependencies
- reproducibility
- beautiful-rust
---
Commit Cargo.lock for binaries and other deployable artifacts so builds
are reproducible.

## Good

- git add Cargo.lock  # in an application or service repo

## Bad

- # .gitignore of a CLI application
Cargo.lock
