---
type: Styleguide Rule
description: Package names should be short, all lowercase, without underscores.
language: python
category: naming
rule_id: PACKAGE-NAMING
priority: warn
tags:
- packages
- pep8
---
Package names should be short, all lowercase, without underscores.

## Good

- renderer/
- sound/
- network/

## Bad

- Renderer/ # Uppercase
- sound_system/ # Underscore
