---
type: Styleguide Rule
description: |-
  Each module should typically contain one primary class, with closely
  related helpers. Module name should match class name in snake_case.
  Exceptions: small related classes, dataclasses, enums.
language: python
category: organization
rule_id: ONE-CLASS-PER-MODULE
priority: info
tags:
- modules
- organization
- clarity
---
Each module should typically contain one primary class, with closely
related helpers. Module name should match class name in snake_case.
Exceptions: small related classes, dataclasses, enums.

## Good

- # entity.py
class Entity:
    pass
- # renderer.py
class Renderer:
    pass

## Bad

- # utils.py
class Entity:
class Renderer:
class Sound:
    pass
