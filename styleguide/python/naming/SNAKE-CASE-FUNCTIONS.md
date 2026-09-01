---
type: Styleguide Rule
description: |-
  Functions and methods should use lowercase with underscores separating
  words. This is Python's standard convention (PEP 8).
language: python
category: naming
rule_id: SNAKE-CASE-FUNCTIONS
priority: error
tags:
- functions
- methods
- pep8
---
Functions and methods should use lowercase with underscores separating
words. This is Python's standard convention (PEP 8).

## Good

- def render_scene():
- def start_sound():
- def read_packets():

## Bad

- def renderScene(): # camelCase
- def RenderScene(): # PascalCase
