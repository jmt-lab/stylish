---
type: Styleguide Rule
description: |-
  Use := to assign and test in one expression when it improves clarity.
  Don't overuse or nest deeply.
language: python
category: control_flow
rule_id: WALRUS-FOR-CLARITY
priority: info
tags:
- walrus
- assignment
- clarity
---
Use := to assign and test in one expression when it improves clarity.
Don't overuse or nest deeply.

## Good

- if (match := pattern.search(text)):
    return match.group(1)
- while (line := file.readline()):
    process(line)

## Bad

- if (x := (y := compute())):
    # Too nested
