---
type: Styleguide Rule
description: |-
  Every package directory must have __init__.py. Use it to expose public
  API, not for implementation. Keep imports explicit.
language: python
category: organization
rule_id: PACKAGE-INIT
priority: warn
tags:
- packages
- api
- exports
---
Every package directory must have __init__.py. Use it to expose public
API, not for implementation. Keep imports explicit.

## Good

- # renderer/__init__.py
from .renderer import Renderer
from .types import RenderMode
__all__ = ['Renderer', 'RenderMode']

## Bad

- # renderer/__init__.py
# Complex implementation code here
