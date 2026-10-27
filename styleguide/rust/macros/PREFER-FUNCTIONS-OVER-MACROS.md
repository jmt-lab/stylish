---
type: Styleguide Rule
description: |-
  When designing an API prefer, in order: regular functions, types,
  traits, and modules; then macro_rules! macros; then other code generation;
  and last proc_macro macros. Macros degrade IDE and code-search support,
  create dialects that are harder to read, and complicate large-scale
  changes, so justify their cost.
language: rust
category: macros
rule_id: PREFER-FUNCTIONS-OVER-MACROS
priority: warn
tags:
- macros
- simplicity
- tooling
- google-style
---
When designing an API prefer, in order: regular functions, types,
traits, and modules; then macro_rules! macros; then other code generation;
and last proc_macro macros. Macros degrade IDE and code-search support,
create dialects that are harder to read, and complicate large-scale
changes, so justify their cost.

## Good

- fn clamp_percent(value: f64) -> f64 {
    value.clamp(0.0, 100.0)
}
- // macro_rules! justified: generates repetitive impls for many types
macro_rules! impl_unit {
    ($($ty:ident),*) => { $(impl Unit for $ty {})* };
}
impl_unit!(Meters, Seconds, Grams);

## Bad

- macro_rules! clamp_percent {
    ($v:expr) => { if $v < 0.0 { 0.0 } else if $v > 100.0 { 100.0 } else { $v } };
}
- #[proc_macro_derive(Getters)] // when plain methods or macro_rules! would do
