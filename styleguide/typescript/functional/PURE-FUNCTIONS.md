---
type: Styleguide Rule
description: |-
  Functions should only read inputs and return outputs without side effects.
  Pure functions are predictable, testable, and composable.
language: typescript
category: functional
rule_id: PURE-FUNCTIONS
priority: warn
tags:
- purity
- side-effects
- testability
---
Functions should only read inputs and return outputs without side effects.
Pure functions are predictable, testable, and composable.

## Good

- function normalize(v: Vector3): Vector3 {
  const len = length(v);
  return { x: v.x/len, y: v.y/len, z: v.z/len };
}

## Bad

- function normalize(v: Vector3): void {
  const len = length(v);
  v.x /= len; v.y /= len; v.z /= len;
}
