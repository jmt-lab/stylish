---
type: Styleguide Rule
description: |-
  For real-time applications (games, audio, video), worst-case
  performance matters more than average. Avoid variable performance.
language: rust
category: optimization
rule_id: WORST-CASE-MATTERS
priority: error
tags:
- optimization
- real-time
- carmack
---
For real-time applications (games, audio, video), worst-case
performance matters more than average. Avoid variable performance.

## Good

- // Consistent 14ms frame time
fn update(&mut self) { ... }

## Bad

- // Average 10ms, spikes to 40ms (dropped frames)
