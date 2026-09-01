---
type: Styleguide Rule
description: |-
  Code that executes the same path consistently is easier to
  understand and optimize. Minimize branching.
language: typescript
category: control_flow
rule_id: TS-LINEAR-FLOW
priority: info
tags:
- linearity
- predictability
- optimization
---
Code that executes the same path consistently is easier to
understand and optimize. Minimize branching.

## Good

- const result = compute();
if (shouldApply) apply(result);

## Bad

- if (cond1) {
  if (cond2) { pathA(); } else { pathB(); }
} else {
  if (cond3) { pathC(); } else { pathD(); }
}
