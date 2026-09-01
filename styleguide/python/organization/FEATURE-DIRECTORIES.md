---
type: Styleguide Rule
description: |-
  Structure directories by feature or subsystem, not by type.
  Prefer renderer/ over models/, views/, controllers/.
language: python
category: organization
rule_id: FEATURE-DIRECTORIES
priority: warn
tags:
- directories
- architecture
- organization
---
Structure directories by feature or subsystem, not by type.
Prefer renderer/ over models/, views/, controllers/.

## Good

- renderer/
  renderer.py
  types.py
  shaders.py
- entity/
  entity.py
  components.py

## Bad

- models/
  renderer_model.py
  entity_model.py
views/
  renderer_view.py
