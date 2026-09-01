---
type: Styleguide Rule
description: |-
  Break complex operations into small, pure functions that compose.
  Each function does one thing without side effects.
language: language-agnostic
category: functional_patterns
rule_id: SMALL-PURE-FUNCTIONS
priority: info
tags:
- composition
- modularity
- purity
---
Break complex operations into small, pure functions that compose.
Each function does one thing without side effects.

## Good

- result = Normalize(Transform(Filter(input)));

## Bad

- void DoEverything(Input& input) {
    // 200 lines mutating input
}
