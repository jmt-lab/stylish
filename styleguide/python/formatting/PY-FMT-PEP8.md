---
type: Styleguide Rule
description: Adhere to PEP 8 style guide conventions. Use automated tools (flake8, pylint) to enforce.
language: python
category: formatting
rule_id: PY-FMT-PEP8
priority: error
tags:
- formatting
- pep8
- standards
---
Adhere to PEP 8 style guide conventions. Use automated tools (flake8, pylint) to enforce.

## Good

- x = 1
- if x == 1:
- def function(arg):

## Bad

- x=1
- if x==1:
- def function( arg ):
