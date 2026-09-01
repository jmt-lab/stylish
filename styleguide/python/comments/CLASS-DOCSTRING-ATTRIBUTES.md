---
type: Styleguide Rule
description: Class docstrings should document public attributes in an Attributes section, especially when they form part of the public API.
language: python
category: comments
rule_id: CLASS-DOCSTRING-ATTRIBUTES
priority: warn
tags:
- docstrings
- classes
- attributes
---
Class docstrings should document public attributes in an Attributes section, especially when they form part of the public API.

## Good

- class Entity:
    """Game entity with position and velocity.
    
    Attributes:
        position: Current (x, y, z) coordinates.
        velocity: Movement vector per frame.
        health: Hit points remaining (0-100).
    """
