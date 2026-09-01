---
type: Styleguide Rule
description: |-
  Module names should be short, lowercase, without underscores if possible.
  Use underscores only if it improves readability.
language: python
category: naming
rule_id: MODULE-NAMING
priority: warn
tags:
- modules
- pep8
---
Module names should be short, lowercase, without underscores if possible.
Use underscores only if it improves readability.

## Good

- renderer.py
- sound.py
- file_utils.py # Underscore for clarity

## Bad

- Renderer.py # Uppercase
- render_scene_manager.py # Too long
