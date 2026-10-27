---
type: Styleguide Rule
description: |-
  Prefer structs with named fields over tuples and multi-field tuple
  structs; .0/.1 indexes quickly become confusing. Exceptions: single-field
  newtype structs, and very local contexts where there is no confusion.
language: rust
category: types
rule_id: NAMED-FIELDS-OVER-TUPLES
priority: warn
tags:
- types
- structs
- readability
- google-style
---
Prefer structs with named fields over tuples and multi-field tuple
structs; .0/.1 indexes quickly become confusing. Exceptions: single-field
newtype structs, and very local contexts where there is no confusion.

## Good

- pub struct Bounds { pub min: f64, pub max: f64 }

fn bounds(values: &[f64]) -> Bounds { ... }
- pub struct Meters(f64);

## Bad

- fn bounds(values: &[f64]) -> (f64, f64) { ... }

let range = bounds(&values).1 - bounds(&values).0; // which is which?
- pub struct Span(usize, usize, u32);
