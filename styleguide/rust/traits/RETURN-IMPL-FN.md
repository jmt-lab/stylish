---
type: Styleguide Rule
description: |-
  Return closures as impl Fn, FnMut, or FnOnce, not Box<dyn Fn>, unless
  callers must store heterogeneous closures together. impl Fn avoids the
  allocation and lets the compiler inline the call.
language: rust
category: traits
rule_id: RETURN-IMPL-FN
priority: info
tags:
- traits
- closures
- performance
- rust-skills
---
Return closures as impl Fn, FnMut, or FnOnce, not Box<dyn Fn>, unless
callers must store heterogeneous closures together. impl Fn avoids the
allocation and lets the compiler inline the call.

## Good

- fn make_scaler(factor: f64) -> impl Fn(f64) -> f64 {
    move |value| value * factor
}

## Bad

- fn make_scaler(factor: f64) -> Box<dyn Fn(f64) -> f64> {
    Box::new(move |value| value * factor)
}
