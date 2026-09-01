---
type: Styleguide Rule
description: |-
  Catch specific error types, not generic Error. Makes error handling
  more precise and prevents catching programmer errors.
language: typescript
category: error_handling
rule_id: NARROW-ERROR-TYPES
priority: warn
tags:
- error-handling
- type-safety
- precision
---
Catch specific error types, not generic Error. Makes error handling
more precise and prevents catching programmer errors.

## Good

- try { ... } catch (e) { if (e instanceof NetworkError) { retry(); } else throw; }
- const result = await fetch(url).catch((e: NetworkError) => ...);

## Bad

- try { ... } catch (e) { /* catches everything including programmer errors */ }
