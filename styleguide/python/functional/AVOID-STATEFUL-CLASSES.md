---
type: Styleguide Rule
description: |-
  Don't create classes just to hold state for a single operation. Use
  functions with parameters. Classes should represent entities with
  meaningful lifecycle.
language: python
category: functional
rule_id: AVOID-STATEFUL-CLASSES
priority: info
tags:
- stateless
- simplicity
- design
---
Don't create classes just to hold state for a single operation. Use
functions with parameters. Classes should represent entities with
meaningful lifecycle.

## Good

- def calculate_distance(a: Vector3, b: Vector3) -> float:
    return math.sqrt((a.x-b.x)**2 + (a.y-b.y)**2 + (a.z-b.z)**2)

## Bad

- class DistanceCalculator:
    def __init__(self):
        self.last_a = None
        self.last_b = None
    def calculate(self, a, b):
        self.last_a = a
        self.last_b = b
        return ...
