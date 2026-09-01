---
type: Styleguide Rule
description: |-
  Avoid deep package hierarchies. Two levels is usually enough.
  Deep nesting makes imports verbose and navigation harder.
language: python
category: organization
rule_id: FLAT-BETTER-NESTED
priority: info
tags:
- packages
- simplicity
- navigation
---
Avoid deep package hierarchies. Two levels is usually enough.
Deep nesting makes imports verbose and navigation harder.

## Good

- myapp/renderer/core.py

## Bad

- myapp/graphics/rendering/opengl/core/renderer.py
