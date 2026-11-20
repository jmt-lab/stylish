---
type: Styleguide Rule
description: |-
  Capture macro_rules! inputs with the most precise fragment specifier
  that fits (expr, ident, ty, path, literal, block, pat). Use raw tt
  munching only when no specifier works, so callers get real parse errors
  instead of confusing expansion failures.
language: rust
category: macros
rule_id: MACRO-FRAGMENT-SPECIFIERS
priority: info
tags:
- macros
- macro-rules
- rust-skills
---
Capture macro_rules! inputs with the most precise fragment specifier
that fits (expr, ident, ty, path, literal, block, pat). Use raw tt
munching only when no specifier works, so callers get real parse errors
instead of confusing expansion failures.

## Good

- macro_rules! newtype_id {
    ($name:ident, $inner:ty) => {
        pub struct $name($inner);
    };
}

## Bad

- macro_rules! newtype_id {
    ($($tokens:tt)*) => { /* re-parses everything by hand */ };
}
