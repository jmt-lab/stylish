---
type: Styleguide Rule
description: |-
  Deeply nested code is hard to reason about. Use early returns,
  extract functions, or restructure to reduce nesting.
language: python
category: control_flow
rule_id: LIMIT-NESTING
priority: warn
tags:
- nesting
- complexity
- readability
---
Deeply nested code is hard to reason about. Use early returns,
extract functions, or restructure to reduce nesting.

## Good

- if not valid:
    return
for item in items:
    if item.ready:
        process(item)

## Bad

- if valid:
    for item in items:
        if item.ready:
            if item.enabled:
                if item.active:
                    process(item)
