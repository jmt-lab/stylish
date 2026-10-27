---
type: Styleguide Rule
description: |-
  Macros must not change a type's kind, alter a function's signature, add
  or remove async, or hide control flow (return, ?, mutation) at the call site.
  Make macro input look like the code it generates.
language: rust
category: macros
rule_id: MACROS-DONT-LIE
priority: warn
tags:
- macros
- predictability
- beautiful-rust
---
Macros must not change a type's kind, alter a function's signature, add
or remove async, or hide control flow (return, ?, mutation) at the call site.
Make macro input look like the code it generates.

## Good

- bitflags! {
    pub struct Mode: u8 { const READ = 1; const WRITE = 2; }
} // input reads like the struct it emits

## Bad

- #[make_async] // silently turns a sync fn into an async one
fn fetch(id: Id) -> Item { ... }
- macro_rules! check { ($e:expr) => { if !$e { return; } }; } // hidden return
