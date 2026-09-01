---
type: Styleguide Rule
description: |-
  Use __all__ to explicitly declare public interface. Makes API
  boundaries clear and controls 'from module import *'.
language: python
category: organization
rule_id: EXPLICIT-EXPORTS
priority: warn
tags:
- api
- exports
- clarity
---
Use __all__ to explicitly declare public interface. Makes API
boundaries clear and controls 'from module import *'.

## Good

- __all__ = ['Renderer', 'RenderMode']

class Renderer:
    pass

## Bad

- # No __all__, everything is implicitly public
