---
type: Styleguide Rule
description: |-
  Each module should import only what it needs. Avoid importing
  entire packages when you need one function.
language: python
category: organization
rule_id: MINIMIZE-MODULE-DEPS
priority: warn
tags:
- imports
- dependencies
- performance
---
Each module should import only what it needs. Avoid importing
entire packages when you need one function.

## Good

- from os.path import join, exists
- from collections.abc import Sequence

## Bad

- import os  # When you only need os.path.join
