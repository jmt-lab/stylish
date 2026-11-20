---
type: Styleguide Rule
description: |-
  Inside macro_rules! macros, refer to your own crate's items as
  $crate::path and to std items with absolute ::std or ::core paths, so
  the macro works no matter what the caller has imported or renamed.
language: rust
category: macros
rule_id: MACRO-DOLLAR-CRATE-PATHS
priority: warn
tags:
- macros
- hygiene
- macro-rules
- rust-skills
---
Inside macro_rules! macros, refer to your own crate's items as
$crate::path and to std items with absolute ::std or ::core paths, so
the macro works no matter what the caller has imported or renamed.

## Good

- #[macro_export]
macro_rules! ensure_positive {
    ($value:expr) => {
        $crate::check::ensure_positive($value, ::core::stringify!($value))
    };
}

## Bad

- #[macro_export]
macro_rules! ensure_positive {
    ($value:expr) => {
        check::ensure_positive($value, stringify!($value)) // breaks outside this crate
    };
}
