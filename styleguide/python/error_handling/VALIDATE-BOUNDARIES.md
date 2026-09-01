---
type: Styleguide Rule
description: |-
  Validate all external input (files, network, user input, APIs) at
  system boundaries. Never trust external data.
language: python
category: error_handling
rule_id: VALIDATE-BOUNDARIES
priority: error
tags:
- validation
- security
- boundaries
---
Validate all external input (files, network, user input, APIs) at
system boundaries. Never trust external data.

## Good

- def load_config(path):
    if not path.exists():
        raise FileNotFoundError(f'Config not found: {path}')
    if path.stat().st_size > MAX_SIZE:
        raise ValueError('Config too large')

## Bad

- def load_config(path):
    return json.load(open(path))  # No validation
