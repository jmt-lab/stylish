---
type: Styleguide Rule
description: |-
  SIMD optimization should target profiled hot paths, not be applied
  speculatively. SIMD adds complexity; ensure payoff is real.
language: language-agnostic
category: optimization
rule_id: SIMD-WHEN-MEASURED
priority: warn
tags:
- simd
- vectorization
- measurement
---
SIMD optimization should target profiled hot paths, not be applied
speculatively. SIMD adds complexity; ensure payoff is real.

## Good

- // Profiled: vector math is 25% of time
// Now add SSE version

## Bad

- // Let's SIMD everything! (No measurement)
