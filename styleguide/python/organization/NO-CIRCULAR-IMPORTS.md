---
type: Styleguide Rule
description: |-
  Design modules to avoid circular dependencies. Use dependency
  inversion, forward references (TYPE_CHECKING), or restructure.
language: python
category: organization
rule_id: NO-CIRCULAR-IMPORTS
priority: error
tags:
- imports
- dependencies
- architecture
---
Design modules to avoid circular dependencies. Use dependency
inversion, forward references (TYPE_CHECKING), or restructure.

## Good

- from typing import TYPE_CHECKING
if TYPE_CHECKING:
    from .entity import Entity

## Bad

- # a.py imports b.py
# b.py imports a.py
