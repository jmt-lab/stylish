---
type: Styleguide Rule
description: |-
  Name features after what they enable, without placeholder words: serde,
  std, alloc, tls, test-util. Not use-serde, with-std, or enable-tls.
  Optional serde support lives behind a feature named exactly serde.
language: rust
category: cargo
rule_id: BARE-FEATURE-NAMES
priority: info
tags:
- cargo
- features
- naming
- official
- beautiful-rust
---
Name features after what they enable, without placeholder words: serde,
std, alloc, tls, test-util. Not use-serde, with-std, or enable-tls.
Optional serde support lives behind a feature named exactly serde.

## Good

- [features]
serde = ["dep:serde"]
tls = ["dep:rustls"]

## Bad

- [features]
use-serde = ["dep:serde"]
enable-tls = ["dep:rustls"]
