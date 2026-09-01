---
type: Styleguide Rule
description: Use PEP 484 type hints instead of documenting types in docstrings. Only include types in docstrings for legacy Python 2 codebases.
language: python
category: comments
rule_id: TYPE-HINTS-OVER-DOCSTRING-TYPES
priority: info
tags:
- type-hints
- modern-python
- documentation
---
Use PEP 484 type hints instead of documenting types in docstrings. Only include types in docstrings for legacy Python 2 codebases.

## Good

- def process(data: List[int]) -> bool:
    """Process integer list.
    
    Args:
        data: Values to process for threshold detection.
    
    Returns:
        Whether processing completed without errors.
    """

## Bad

- def process(data):
    """Process integer list.
    
    Args:
        data (List[int]): List of integers.
    
    Returns:
        bool: Success status.
    """
