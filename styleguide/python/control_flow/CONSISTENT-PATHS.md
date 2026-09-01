---
type: Styleguide Rule
description: |-
  Code that executes the same path most of the time is easier to
  understand and optimize. Minimize branching.
language: python
category: control_flow
rule_id: CONSISTENT-PATHS
priority: info
tags:
- consistency
- predictability
- optimization
---
Code that executes the same path most of the time is easier to
understand and optimize. Minimize branching.

## Good

- result = compute()
if should_apply:
    apply(result)
return result

## Bad

- if cond1:
    if cond2:
        return path_a()
    return path_b()
return path_c()
