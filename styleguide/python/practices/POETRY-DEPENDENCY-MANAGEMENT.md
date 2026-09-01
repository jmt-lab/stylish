---
type: Styleguide Rule
description: |-
  Poetry handles dependencies, virtual environments, and packaging.
  Simpler than pip-tools. Use pyproject.toml for configuration.
language: python
category: practices
rule_id: POETRY-DEPENDENCY-MANAGEMENT
priority: info
tags:
- poetry
- dependencies
- tooling
---
Poetry handles dependencies, virtual environments, and packaging.
Simpler than pip-tools. Use pyproject.toml for configuration.

## Good

- poetry add requests
poetry install

## Bad

- # Manual pip install
# No lock file
