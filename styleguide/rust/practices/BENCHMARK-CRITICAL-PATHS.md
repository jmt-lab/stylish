---
type: Styleguide Rule
description: |-
  Carmack: profile first. Use criterion for benchmarking critical
  code paths. Track performance over time.
language: rust
category: practices
rule_id: BENCHMARK-CRITICAL-PATHS
priority: warn
tags:
- practices
- benchmarking
- carmack
---
Carmack: profile first. Use criterion for benchmarking critical
code paths. Track performance over time.

## Good

- // benches/my_benchmark.rs
use criterion::{criterion_group, Criterion};
fn bench_render(c: &mut Criterion) { ... }

## Bad

- # No benchmarks for critical code
