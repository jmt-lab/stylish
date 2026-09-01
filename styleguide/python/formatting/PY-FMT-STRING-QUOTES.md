---
type: Styleguide Rule
description: Be consistent with string quotes. Black normalizes to double quotes. Avoid mixing unless necessary.
language: python
category: formatting
rule_id: PY-FMT-STRING-QUOTES
priority: info
tags:
- formatting
- consistency
- strings
---
Be consistent with string quotes. Black normalizes to double quotes. Avoid mixing unless necessary.

## Good

- message = "Hello, world"
- sql = "SELECT * FROM table WHERE name = 'value'"


## Bad

- message = "Hello" + 'world'

