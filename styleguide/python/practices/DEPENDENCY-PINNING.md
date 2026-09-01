---
type: Styleguide Rule
description: |-
  Use poetry or pip-tools to pin exact versions. Lock files ensure
  reproducible builds. Update dependencies deliberately.
language: python
category: practices
rule_id: DEPENDENCY-PINNING
priority: error
tags:
- dependencies
- reproducibility
- stability
---
Use poetry or pip-tools to pin exact versions. Lock files ensure
reproducible builds. Update dependencies deliberately.

## Good

- # poetry.lock or requirements.txt with pinned versions

## Bad

- # requirements.txt with >= operators
