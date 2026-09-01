---
type: Styleguide Rule
description: |-
  Class names should use PascalCase (CapWords convention). No underscores
  unless required for clarity.
language: python
category: naming
rule_id: PASCAL-CASE-CLASSES
priority: error
tags:
- classes
- pep8
---
Class names should use PascalCase (CapWords convention). No underscores
unless required for clarity.

## Good

- class RenderEntity:
- class SoundManager:
- class HTTPConnection:

## Bad

- class render_entity: # snake_case
- class renderEntity: # camelCase
