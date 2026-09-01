---
type: Styleguide Rule
description: |-
  Reduce the amount of code under conditionals. Use early returns to
  keep the main path at base indentation. Don't nest deeply.
language: language-agnostic
category: control_flow
rule_id: MINIMIZE-AREA-UNDER-IFS
priority: warn
tags:
- conditionals
- nesting
- readability
---
Reduce the amount of code under conditionals. Use early returns to
keep the main path at base indentation. Don't nest deeply.

## Good

- if (!IsValid(entity)) {
    return;
}
// Main logic at base level
Process(entity);

## Bad

- if (IsValid(entity)) {
    // 50 lines nested
    Process(entity);
}
