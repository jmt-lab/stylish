---
type: Styleguide Rule
description: |-
  Always profile to find actual bottlenecks before optimizing. Don't
  guess — optimization based on intuition often targets wrong code.
  Modern CPUs are complex; what seems faster may be slower. Always
  measure with real data and real hardware. Test both approaches and
  let evidence drive decisions.
language: language-agnostic
category: optimization
rule_id: PROFILE-FIRST
priority: error
tags:
- profiling
- measurement
- data-driven
- validation
- evidence
---
Always profile to find actual bottlenecks before optimizing. Don't
guess — optimization based on intuition often targets wrong code.
Modern CPUs are complex; what seems faster may be slower. Always
measure with real data and real hardware. Test both approaches and
let evidence drive decisions.

## Good

- // Profiled, this function is 40% of frame time
// Now optimize
- // Tested both approaches, version A is 2x faster

## Bad

- // This looks slow, let me optimize
// (Actually 0.1% of runtime)
- // This should be faster (never measured)
