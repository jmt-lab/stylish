---
type: Styleguide Rule
description: Every Python file should start with a module docstring describing its purpose and contents. Include usage examples for complex modules.
language: python
category: comments
rule_id: MODULE-DOCSTRING
priority: warn
tags:
- docstrings
- modules
- documentation
---
Every Python file should start with a module docstring describing its purpose and contents. Include usage examples for complex modules.

## Good

- """Geometry utilities for 3D rendering.

Provides vector math, matrix operations, and collision detection
for the rendering pipeline.
"""

## Bad

- # geometry.py
# math stuff
