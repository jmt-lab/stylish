---
type: Styleguide Rule
description: |-
  Don't encode type information in variable names. Python is dynamically
  typed and type hints provide type information when needed.
language: python
category: naming
rule_id: TYPE-SUFFIX-AVOID
priority: warn
tags:
- variables
- antipattern
---
Don't encode type information in variable names. Python is dynamically
typed and type hints provide type information when needed.

## Good

- entities = []
- entity_map = {}
- name = 'player'

## Bad

- entities_list = [] # Redundant suffix
- entity_dict = {} # Type in name
- name_str = 'player' # Unnecessary
