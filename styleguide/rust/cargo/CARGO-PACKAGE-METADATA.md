---
type: Styleguide Rule
description: |-
  Published crates fill in the [package] metadata that crates.io and
  docs.rs show: description, license, repository, readme, keywords,
  categories, and rust-version (Clippy: cargo_common_metadata). Internal
  crates set publish = false instead.
language: rust
category: cargo
rule_id: CARGO-PACKAGE-METADATA
priority: warn
tags:
- cargo
- publishing
- metadata
- rust-skills
---
Published crates fill in the [package] metadata that crates.io and
docs.rs show: description, license, repository, readme, keywords,
categories, and rust-version (Clippy: cargo_common_metadata). Internal
crates set publish = false instead.

## Good

- [package]
name = "fastcsv"
version = "0.3.1"
edition = "2024"
rust-version = "1.85"
description = "A zero-copy CSV parser"
license = "MIT OR Apache-2.0"
repository = "https://github.com/example/fastcsv"
readme = "README.md"
keywords = ["csv", "parser"]
categories = ["parser-implementations"]

- [package]
name = "billing-internal"
publish = false

## Bad

- [package]
name = "fastcsv"
version = "0.3.1"
edition = "2024"
# no description, license, or repository: crates.io rejects the publish
