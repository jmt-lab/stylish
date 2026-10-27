---
type: Styleguide Rule
description: |-
  Keep a proc-macro crate as a thin shim over a normal library crate that
  holds the logic and its tests (snapshot tests with insta, error-message
  tests with trybuild). Prefer a derive macro over a proc macro that emits
  new hidden types.
language: rust
category: macros
rule_id: PROC-MACRO-THIN-SHIM
priority: info
tags:
- macros
- proc-macro
- testing
- beautiful-rust
---
Keep a proc-macro crate as a thin shim over a normal library crate that
holds the logic and its tests (snapshot tests with insta, error-message
tests with trybuild). Prefer a derive macro over a proc macro that emits
new hidden types.

## Good

- crates/
  foo/              # re-exports the derive
  foo-macros/       # #[proc_macro_derive] shims only
  foo-macros-impl/  # token transformation + insta/trybuild tests

## Bad

- // foo-macros/src/lib.rs: 2,000 lines of untested token manipulation
