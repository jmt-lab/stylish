---
type: Styleguide Rule
description: |-
  Rather than branching on whether to execute code, execute consistently
  and use flags to control effects. This creates predictable execution.
language: language-agnostic
category: functional_patterns
rule_id: EXECUTE-AND-INHIBIT
priority: info
tags:
- control-flow
- consistency
- predictability
---
Rather than branching on whether to execute code, execute consistently
and use flags to control effects. This creates predictable execution.

## Good

- result = Compute(input);
if (shouldApply) { Apply(result); }

## Bad

- if (shouldCompute) {
    result = Compute(input);
    Apply(result);
}
