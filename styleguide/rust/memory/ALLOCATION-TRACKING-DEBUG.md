---
type: Styleguide Rule
description: |-
  In debug builds, consider using allocator instrumentation to track
  allocation patterns and find leaks.
language: rust
category: memory
rule_id: ALLOCATION-TRACKING-DEBUG
priority: info
tags:
- memory
- debugging
- carmack
---
In debug builds, consider using allocator instrumentation to track
allocation patterns and find leaks.

## Good

- #[cfg(debug_assertions)]
use tracking_allocator::AllocationTracker;

## Bad

- // No allocation tracking, harder to find leaks
