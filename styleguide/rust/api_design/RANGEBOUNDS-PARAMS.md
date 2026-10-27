---
type: Styleguide Rule
description: |-
  Accept impl RangeBounds<T> instead of (low, high) pairs or separate
  start/end parameters, so callers can write 1..3, 1.., ..=5, or ..
language: rust
category: api_design
rule_id: RANGEBOUNDS-PARAMS
priority: info
tags:
- api-design
- parameters
- ranges
- beautiful-rust
---
Accept impl RangeBounds<T> instead of (low, high) pairs or separate
start/end parameters, so callers can write 1..3, 1.., ..=5, or ..

## Good

- pub fn lines(&self, range: impl RangeBounds<usize>) -> impl Iterator<Item = &str> { ... }

## Bad

- pub fn lines(&self, start: usize, end: usize) -> impl Iterator<Item = &str> { ... }
