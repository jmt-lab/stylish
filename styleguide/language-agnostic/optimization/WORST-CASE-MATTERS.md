---
type: Styleguide Rule
description: |-
  For real-time applications (60fps target), worst-case performance
  matters more than average case. Avoid highly variable performance.
language: language-agnostic
category: optimization
rule_id: WORST-CASE-MATTERS
priority: error
tags:
- real-time
- consistency
- framerate
---
For real-time applications (60fps target), worst-case performance
matters more than average case. Avoid highly variable performance.

## Good

- // Consistent 14ms frame time

## Bad

- // Average 10ms, spikes to 40ms (frame drops)
