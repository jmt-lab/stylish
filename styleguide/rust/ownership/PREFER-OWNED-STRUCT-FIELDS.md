---
type: Styleguide Rule
description: |-
  Prefer owned data (String, Vec<u8>, PathBuf) in structs over references.
  A struct holding &'a T forces a lifetime onto every container that holds it,
  and owning is rarely the bottleneck. Borrow in structs only for short-lived
  views (parsers, iterators) or when profiling demands it.
language: rust
category: ownership
rule_id: PREFER-OWNED-STRUCT-FIELDS
priority: info
tags:
- ownership
- lifetimes
- structs
- beautiful-rust
---
Prefer owned data (String, Vec<u8>, PathBuf) in structs over references.
A struct holding &'a T forces a lifetime onto every container that holds it,
and owning is rarely the bottleneck. Borrow in structs only for short-lived
views (parsers, iterators) or when profiling demands it.

## Good

- pub struct Request { path: String, headers: Vec<Header> }
- pub struct Tokenizer<'src> { input: &'src str, pos: usize } // short-lived view

## Bad

- pub struct Request<'a> { path: &'a str, headers: &'a [Header] } // long-lived; lifetime spreads everywhere
