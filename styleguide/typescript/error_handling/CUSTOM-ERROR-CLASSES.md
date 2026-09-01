---
type: Styleguide Rule
description: |-
  Define custom error classes to distinguish error categories. Makes error
  handling more precise and type-safe.
language: typescript
category: error_handling
rule_id: CUSTOM-ERROR-CLASSES
priority: warn
tags:
- error-types
- type-safety
- maintainability
---
Define custom error classes to distinguish error categories. Makes error
handling more precise and type-safe.

## Good

- class ValidationError extends Error { constructor(field: string) { ... } }
- class NetworkError extends Error { constructor(code: number) { ... } }
- if (error instanceof ValidationError) { ... }

## Bad

- throw new Error('validation:field'); // String parsing
