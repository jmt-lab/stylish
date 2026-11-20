---
type: Styleguide Rule
description: |-
  Use const for values that are inlined at each use, such as numbers,
  strings, and small tables. Use static only when the value needs one
  fixed address or interior mutability, such as an atomic, Mutex, or
  OnceLock. Never use static just to avoid copying a small constant.
language: rust
category: constructs
rule_id: CONST-VS-STATIC
priority: warn
tags:
- constants
- statics
- globals
- rust-skills
---
Use const for values that are inlined at each use, such as numbers,
strings, and small tables. Use static only when the value needs one
fixed address or interior mutability, such as an atomic, Mutex, or
OnceLock. Never use static just to avoid copying a small constant.

## Good

- const MAX_RETRIES: u32 = 5;
static CONNECTIONS: AtomicUsize = AtomicUsize::new(0);
static GEO_DATABASE: OnceLock<GeoDatabase> = OnceLock::new();

## Bad

- static MAX_RETRIES: u32 = 5;               // no reason for an address
const CONNECTIONS: AtomicUsize = AtomicUsize::new(0); // a new atomic at every use
