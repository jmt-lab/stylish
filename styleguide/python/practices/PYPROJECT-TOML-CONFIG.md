---
type: Styleguide Rule
description: |-
  Use pyproject.toml for tool configuration. Single source for
  ruff, mypy, pytest, coverage settings.
language: python
category: practices
rule_id: PYPROJECT-TOML-CONFIG
priority: info
tags:
- configuration
- centralization
- pyproject
---
Use pyproject.toml for tool configuration. Single source for
ruff, mypy, pytest, coverage settings.

## Good

- [tool.mypy]
strict = true
[tool.ruff]
line-length = 100

## Bad

- # Scattered config files: setup.cfg, .flake8, mypy.ini
