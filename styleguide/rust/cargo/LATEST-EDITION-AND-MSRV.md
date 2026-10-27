---
type: Styleguide Rule
description: |-
  New crates use the latest stable edition and set rust-version
  deliberately at creation; raise the MSRV conservatively.
language: rust
category: cargo
rule_id: LATEST-EDITION-AND-MSRV
priority: info
tags:
- cargo
- edition
- msrv
- beautiful-rust
---
New crates use the latest stable edition and set rust-version
deliberately at creation; raise the MSRV conservatively.

## Good

- [package]
edition = "2024"
rust-version = "1.85"

## Bad

- [package]
edition = "2018"  # new crate, old edition, no rust-version
