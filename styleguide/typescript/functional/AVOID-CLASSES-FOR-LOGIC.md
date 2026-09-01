---
type: Styleguide Rule
description: |-
  Use classes for entities with identity. Use functions for stateless
  logic. Classes encourage hidden mutable state. Utility functions should
  not maintain state — stateless functions are easier to test, parallelize,
  and reuse safely.
language: typescript
category: functional
rule_id: AVOID-CLASSES-FOR-LOGIC
priority: info
tags:
- classes
- functions
- state
- stateless
- utilities
- simplicity
---
Use classes for entities with identity. Use functions for stateless
logic. Classes encourage hidden mutable state. Utility functions should
not maintain state — stateless functions are easier to test, parallelize,
and reuse safely.

## Good

- export function calculateScore(game: Game): number
- export function distance(a: Vector3, b: Vector3): number

## Bad

- class ScoreCalculator {
  calculate(game: Game): number
}
- class DistanceCalculator {
  private lastA: Vector3;
  calculate(a: Vector3, b: Vector3): number
}
