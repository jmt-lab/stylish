---
type: Styleguide Rule
description: |-
  Caught errors should be typed as unknown, forcing explicit type checking.
  Never use any for error handling.
language: typescript
category: error_handling
rule_id: UNKNOWN-NOT-ANY
priority: error
tags:
- type-safety
- error-handling
- unknown
---
Caught errors should be typed as unknown, forcing explicit type checking.
Never use any for error handling.

## Good

- try { ... } catch (e: unknown) { if (e instanceof Error) { ... } }
- const err = e as Error; // Explicit cast after check

## Bad

- try { ... } catch (e: any) { e.message; } // Unsafe
