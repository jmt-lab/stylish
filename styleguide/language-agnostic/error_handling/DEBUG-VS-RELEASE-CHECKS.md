---
type: Styleguide Rule
description: |-
  Expensive validation should be debug-only (assertions). Critical
  safety checks should be release-enabled (explicit if checks).
language: language-agnostic
category: error_handling
rule_id: DEBUG-VS-RELEASE-CHECKS
priority: warn
tags:
- performance
- safety
- debugging
---
Expensive validation should be debug-only (assertions). Critical
safety checks should be release-enabled (explicit if checks).

## Good

- assert(ValidateComplexInvariant()); // Debug only
- if (ptr == NULL) return ERROR; // Always checked

## Bad

- #ifdef DEBUG
if (ptr == NULL) return ERROR;
#endif // Safety check should always run
