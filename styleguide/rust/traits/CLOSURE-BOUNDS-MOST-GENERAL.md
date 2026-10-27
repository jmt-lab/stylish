---
type: Styleguide Rule
description: |-
  Accept closures with the most general bound that works: FnOnce if called
  once, FnMut if called repeatedly with mutation, Fn otherwise. Prefer Fn*
  bounds over bare fn pointers, which can't capture state. Put a closure
  parameter last and take at most one.
language: rust
category: traits
rule_id: CLOSURE-BOUNDS-MOST-GENERAL
priority: info
tags:
- traits
- closures
- generics
- beautiful-rust
---
Accept closures with the most general bound that works: FnOnce if called
once, FnMut if called repeatedly with mutation, Fn otherwise. Prefer Fn*
bounds over bare fn pointers, which can't capture state. Put a closure
parameter last and take at most one.

## Good

- pub fn retry<T, F: FnMut() -> Result<T, Error>>(attempts: u32, op: F) -> Result<T, Error> { ... }
- pub fn get_or_insert_with(&mut self, key: K, make: impl FnOnce() -> V) -> &V { ... }

## Bad

- pub fn retry<T>(op: fn() -> Result<T, Error>, attempts: u32) -> Result<T, Error> { ... }
- pub fn get_or_insert_with(&mut self, key: K, make: impl Fn() -> V) -> &V { ... } // called once
