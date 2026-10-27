---
type: Styleguide Rule
description: |-
  Don't call std::panic::catch_unwind in first-party code; it only works
  with panic=unwind and must never be relied on for correctness. The only
  exceptions are defense in depth around critical entry points of a codebase
  that already works hard to avoid panics, and stopping panics from unwinding
  across an extern "C" boundary (see FFI-SAFE-BOUNDARY).
language: rust
category: safety
rule_id: NO-CATCH-UNWIND
priority: error
tags:
- safety
- panics
- error-handling
- google-style
---
Don't call std::panic::catch_unwind in first-party code; it only works
with panic=unwind and must never be relied on for correctness. The only
exceptions are defense in depth around critical entry points of a codebase
that already works hard to avoid panics, and stopping panics from unwinding
across an extern "C" boundary (see FFI-SAFE-BOUNDARY).

## Good

- fn parse(input: &str) -> Result<Ast, ParseError> { ... } // report failures as Result

## Bad

- let result = panic::catch_unwind(|| parse(input));
let ast = result.unwrap_or_default(); // relies on unwinding for control flow
