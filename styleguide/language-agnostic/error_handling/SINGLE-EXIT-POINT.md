---
type: Styleguide Rule
description: |-
  For functions with manual resource cleanup in C-style code (no
  RAII/defer), consider using a single exit point with goto cleanup.
  For all other functions, prefer early returns (see EARLY-RETURN in
  control_flow.yaml). This rule is the exception, not the default.
language: language-agnostic
category: error_handling
rule_id: SINGLE-EXIT-POINT
priority: info
tags:
- cleanup
- resources
- safety
---
For functions with manual resource cleanup in C-style code (no
RAII/defer), consider using a single exit point with goto cleanup.
For all other functions, prefer early returns (see EARLY-RETURN in
control_flow.yaml). This rule is the exception, not the default.

## Good

- if (error) goto cleanup;
...
cleanup:
    FreeResources();
    return result;

## Bad

- if (error) return; // Forgot to free resources
