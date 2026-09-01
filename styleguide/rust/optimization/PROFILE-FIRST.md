---
type: Styleguide Rule
description: |-
  Carmack principle: Never optimize without profiling. Use cargo bench,
  flamegraph, perf, or other profilers to find actual bottlenecks.
language: rust
category: optimization
rule_id: PROFILE-FIRST
priority: error
tags:
- optimization
- profiling
- carmack
---
Carmack principle: Never optimize without profiling. Use cargo bench,
flamegraph, perf, or other profilers to find actual bottlenecks.

## Good

- // Profiled: this function is 40% of frame time
// Now optimize

## Bad

- // This looks slow, optimizing without measurement
