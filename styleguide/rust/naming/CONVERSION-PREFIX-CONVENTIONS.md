---
type: Styleguide Rule
description: |-
  Use conversion prefixes with the matching self convention: as_ borrows
  cheaply (&self -> &U), to_ performs a potentially expensive conversion
  (&self, or self for Copy types), and into_ consumes self (Clippy:
  wrong_self_convention).
language: rust
category: naming
rule_id: CONVERSION-PREFIX-CONVENTIONS
priority: warn
tags:
- naming
- conversions
- clippy
- official
- google-style
---
Use conversion prefixes with the matching self convention: as_ borrows
cheaply (&self -> &U), to_ performs a potentially expensive conversion
(&self, or self for Copy types), and into_ consumes self (Clippy:
wrong_self_convention).

## Good

- fn as_bytes(&self) -> &[u8]
fn to_lowercase(&self) -> String
fn into_inner(self) -> T

## Bad

- fn as_string(&self) -> String // allocates: should be to_string
fn to_inner(self) -> T // consumes self: should be into_inner
fn into_slice(&self) -> &[u8] // borrows: should be as_slice
