---
type: Styleguide Rule
description: |-
  Functions should only read inputs and return outputs without side
  effects. No global state access. Pure functions are predictable,
  testable, and thread-safe.
language: language-agnostic
category: functional_patterns
rule_id: PURE-FUNCTIONS
priority: warn
tags:
- purity
- side-effects
- testability
---
Functions should only read inputs and return outputs without side
effects. No global state access. Pure functions are predictable,
testable, and thread-safe.

## Good

- // Pure: only inputs affect output
Vector3 Normalized(const Vector3& v) {
    float len = Length(v);
    return Vector3(v.x/len, v.y/len, v.z/len);
}

## Bad

- // Impure: modifies input
void Normalize(Vector3& v) {
    float len = Length(v);
    v.x /= len; v.y /= len; v.z /= len;
}
