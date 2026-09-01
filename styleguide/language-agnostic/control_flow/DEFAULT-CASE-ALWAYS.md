---
type: Styleguide Rule
description: |-
  Every switch should have a default case, even if it's just an
  assertion or error. This catches unexpected values.
language: language-agnostic
category: control_flow
rule_id: DEFAULT-CASE-ALWAYS
priority: warn
tags:
- switch
- completeness
- safety
---
Every switch should have a default case, even if it's just an
assertion or error. This catches unexpected values.

## Good

- switch (state) {
    case A: ...
    case B: ...
    default: assert(false);
}

## Bad

- switch (state) {
    case A: ...
    case B: ...
} // Missing default
