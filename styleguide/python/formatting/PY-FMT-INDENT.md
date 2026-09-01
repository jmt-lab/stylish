---
type: Styleguide Rule
description: Use 4 spaces per indentation level. Never use tabs.
language: python
category: formatting
rule_id: PY-FMT-INDENT
priority: error
tags:
- formatting
- indentation
- pep8
---
Use 4 spaces per indentation level. Never use tabs.

## Good

- def function():
    return True


## Bad

- def function():
  return True

- def function():
	return True

