---
type: Styleguide Rule
description: |-
  NULL pointer dereferences are the biggest problem in C/C++. Static
  analysis should catch these. Fix all NULL pointer warnings.
language: language-agnostic
category: static_analysis
rule_id: NULL-POINTER-PRIORITY
priority: error
tags:
- null-pointers
- safety
- crashes
---
NULL pointer dereferences are the biggest problem in C/C++. Static
analysis should catch these. Fix all NULL pointer warnings.

## Good

- if (ptr == NULL) return ERROR;
ptr->field = value; // Safe

## Bad

- ptr->field = value; // Analyzer warns: possible NULL
