---
type: Styleguide Rule
description: |-
  Breaking out of nested loops makes control flow hard to follow.
  Use flags, extract to function with return, or restructure.
language: python
category: control_flow
rule_id: BREAK-SINGLE-LEVEL
priority: warn
tags:
- loops
- control-flow
- clarity
---
Breaking out of nested loops makes control flow hard to follow.
Use flags, extract to function with return, or restructure.

## Good

- def find():
    for x in xs:
        for y in ys:
            if match(x, y):
                return (x, y)
    return None

## Bad

- found = False
for x in xs:
    for y in ys:
        if match(x, y):
            found = True
            break
    if found:
        break
