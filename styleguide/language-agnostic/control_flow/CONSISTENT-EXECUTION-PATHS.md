---
type: Styleguide Rule
description: |-
  Code that executes the same path most of the time is easier to
  understand and optimize. Avoid highly branched execution.
language: language-agnostic
category: control_flow
rule_id: CONSISTENT-EXECUTION-PATHS
priority: info
tags:
- consistency
- predictability
- optimization
---
Code that executes the same path most of the time is easier to
understand and optimize. Avoid highly branched execution.

## Good

- // Same path every time
result = Compute();
if (shouldApply) Apply(result);

## Bad

- // Different paths, hard to predict
if (cond1) { if (cond2) { ... } else { ... } }
