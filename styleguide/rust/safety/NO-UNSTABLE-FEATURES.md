---
type: Styleguide Rule
description: |-
  Don't use unstable (nightly-only) language or library features. Any
  exception must be explicitly approved, typically only for features with a
  clear path to stabilization or that are strictly required to build.
language: rust
category: safety
rule_id: NO-UNSTABLE-FEATURES
priority: error
tags:
- safety
- stability
- nightly
- google-style
---
Don't use unstable (nightly-only) language or library features. Any
exception must be explicitly approved, typically only for features with a
clear path to stabilization or that are strictly required to build.

## Good

- let sorted = values.is_sorted(); // stabilized API

## Bad

- #![feature(let_chains)]
#![feature(specialization)]
