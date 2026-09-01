---
type: Styleguide Rule
description: |-
  Prefer explicit loops for performance-critical code and complex
  multi-step logic where the loop body has side effects or complex
  control flow. For simple, stateless collection transforms, functional
  patterns are fine (see MAP-FILTER-REDUCE in functional_patterns.yaml).
language: language-agnostic
category: control_flow
rule_id: EXPLICIT-LOOPS
priority: warn
tags:
- loops
- clarity
- bugs
---
Prefer explicit loops for performance-critical code and complex
multi-step logic where the loop body has side effects or complex
control flow. For simple, stateless collection transforms, functional
patterns are fine (see MAP-FILTER-REDUCE in functional_patterns.yaml).

## Good

- for (int i = 0; i < 4; i++) {
    Process(items[i]);
}

## Bad

- Process(items[0]); Process(items[1]); // Copy-paste bugs
