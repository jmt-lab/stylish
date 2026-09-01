---
type: Styleguide Rule
description: |-
  Use 'with' statements to ensure cleanup happens even on exceptions.
  Prefer context managers over try/finally.
language: python
category: error_handling
rule_id: CONTEXT-MANAGERS
priority: warn
tags:
- cleanup
- resources
- safety
---
Use 'with' statements to ensure cleanup happens even on exceptions.
Prefer context managers over try/finally.

## Good

- with open(path) as f:
    data = f.read()
- with lock:
    critical_section()

## Bad

- f = open(path)
try:
    data = f.read()
finally:
    f.close()
