---
type: Styleguide Rule
description: |-
  Use absolute imports for cross-package references. Relative imports
  are acceptable within the same package for sibling modules only.
language: python
category: organization
rule_id: ABSOLUTE-IMPORTS
priority: info
tags:
- imports
- clarity
---
Use absolute imports for cross-package references. Relative imports
are acceptable within the same package for sibling modules only.

## Good

- from myapp.renderer import Renderer
- from .types import RenderMode  # Within same package

## Bad

- from ...utils import helper  # Too many dots
