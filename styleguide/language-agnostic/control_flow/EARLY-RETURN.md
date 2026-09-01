---
type: Styleguide Rule
description: |-
  Check for error conditions at the start of functions and return early.
  This keeps the happy path at the main indentation level.
language: language-agnostic
category: control_flow
rule_id: EARLY-RETURN
priority: warn
tags:
- errors
- returns
- clarity
---
Check for error conditions at the start of functions and return early.
This keeps the happy path at the main indentation level.

## Good

- if (entity == NULL) return ERROR;
if (!entity->IsValid()) return ERROR;
// Happy path

## Bad

- if (entity != NULL) {
    if (entity->IsValid()) {
        // Happy path nested
    }
}
