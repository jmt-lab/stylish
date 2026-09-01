---
type: Styleguide Rule
description: |-
  Functions should depend only on inputs and return outputs without side
  effects. No global state access, no mutation of inputs. Pure functions
  are testable and predictable.
language: python
category: functional
rule_id: PURE-FUNCTIONS
priority: warn
tags:
- purity
- side-effects
- testability
---
Functions should depend only on inputs and return outputs without side
effects. No global state access, no mutation of inputs. Pure functions
are testable and predictable.

## Good

- def normalize(v: Vector3) -> Vector3:
    length = v.length()
    return Vector3(v.x/length, v.y/length, v.z/length)

## Bad

- def normalize(v: Vector3) -> None:
    length = v.length()
    v.x /= length  # Mutates input
