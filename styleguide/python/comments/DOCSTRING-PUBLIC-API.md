---
type: Styleguide Rule
description: All public modules, classes, functions, and methods must have docstrings. Use Google style format with summary line, optional detailed description, and sections for Args/Returns/Raises.
language: python
category: comments
rule_id: DOCSTRING-PUBLIC-API
priority: error
tags:
- docstrings
- public-api
- documentation
---
All public modules, classes, functions, and methods must have docstrings. Use Google style format with summary line, optional detailed description, and sections for Args/Returns/Raises.

## Good

- def calculate_distance(point_a, point_b):
    """Calculate Euclidean distance between two points.
    
    Args:
        point_a: Tuple of (x, y) coordinates.
        point_b: Tuple of (x, y) coordinates.
    
    Returns:
        Float distance between the points.
    """

## Bad

- def calculate_distance(point_a, point_b):
    # calculates distance
    pass
