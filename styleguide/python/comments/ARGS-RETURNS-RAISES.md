---
type: Styleguide Rule
description: Document parameters and return values in docstrings with behavioral descriptions, but omit type annotations from docstrings when type hints are present (see TYPE-HINTS-OVER-DOCSTRING-TYPES).
language: python
category: comments
rule_id: ARGS-RETURNS-RAISES
priority: error
tags:
- docstrings
- parameters
- contracts
---
Document parameters and return values in docstrings with behavioral descriptions, but omit type annotations from docstrings when type hints are present (see TYPE-HINTS-OVER-DOCSTRING-TYPES).

## Good

- def load_config(path: str | Path) -> dict:
    """Load configuration from file.
    
    Args:
        path: Path to config file.
    
    Returns:
        Parsed configuration mapping.
    
    Raises:
        FileNotFoundError: If config file doesn't exist.
        ValueError: If config format is invalid.
    """

## Bad

- def load_config(path):
    """Load configuration."""
- def load_config(path: str) -> dict:
    """Load configuration.
    
    Args:
        path (str): Path to config file.
    
    Returns:
        dict: Parsed configuration.
    """
