---
type: Styleguide Rule
description: |-
  Implement From / TryFrom, never Into / TryInto directly; the blanket
  impls provide those. Use From only for lossless, infallible conversions and
  TryFrom otherwise. In generic bounds, accept Into<T>.
language: rust
category: traits
rule_id: IMPL-FROM-NOT-INTO
priority: warn
tags:
- traits
- conversions
- clippy
- beautiful-rust
---
Implement From / TryFrom, never Into / TryInto directly; the blanket
impls provide those. Use From only for lossless, infallible conversions and
TryFrom otherwise. In generic bounds, accept Into<T>.

## Good

- impl From<Celsius> for Kelvin { fn from(c: Celsius) -> Self { ... } }
- impl TryFrom<i64> for Port { type Error = InvalidPortError; ... }

## Bad

- impl Into<Kelvin> for Celsius { fn into(self) -> Kelvin { ... } }
- impl From<i64> for Port { ... } // can't fail? truncates silently
