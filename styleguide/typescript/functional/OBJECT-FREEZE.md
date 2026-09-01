---
type: Styleguide Rule
description: |-
  For configuration objects and constants, use Object.freeze to enforce
  immutability at runtime in addition to TypeScript's readonly.
language: typescript
category: functional
rule_id: OBJECT-FREEZE
priority: info
tags:
- freeze
- immutability
- runtime
---
For configuration objects and constants, use Object.freeze to enforce
immutability at runtime in addition to TypeScript's readonly.

## Good

- const CONFIG = Object.freeze({
  apiUrl: 'https://api.example.com',
  timeout: 5000
});

## Bad

- const CONFIG = {
  apiUrl: 'https://api.example.com',
  timeout: 5000
}; // Can be mutated
