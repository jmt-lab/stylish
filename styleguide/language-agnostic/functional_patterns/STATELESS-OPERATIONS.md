---
type: Styleguide Rule
description: |-
  Operations that don't need state shouldn't maintain it. Stateless
  operations are easier to test, parallelize, and reuse.
language: language-agnostic
category: functional_patterns
rule_id: STATELESS-OPERATIONS
priority: info
tags:
- stateless
- simplicity
- reusability
---
Operations that don't need state shouldn't maintain it. Stateless
operations are easier to test, parallelize, and reuse.

## Good

- float Distance(Vector3 a, Vector3 b) // Stateless

## Bad

- class DistanceCalculator {
    Vector3 lastA, lastB;
    float Calculate(Vector3 a, Vector3 b);
} // Unnecessary state
