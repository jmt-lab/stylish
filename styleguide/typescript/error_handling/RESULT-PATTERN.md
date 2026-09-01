---
type: Styleguide Rule
description: |-
  Expected failures should return discriminated union Result types, not throw.
  Makes error handling explicit and type-safe. Expected failures are conditions
  that can occur during normal operation (network errors, validation failures,
  missing resources). Programmer errors are violated invariants, impossible
  states, and type assertion failures.
language: typescript
category: error_handling
rule_id: RESULT-PATTERN
priority: error
tags:
- result-type
- type-safety
- explicit-errors
---
Expected failures should return discriminated union Result types, not throw.
Makes error handling explicit and type-safe. Expected failures are conditions
that can occur during normal operation (network errors, validation failures,
missing resources). Programmer errors are violated invariants, impossible
states, and type assertion failures.

## Good

- type Result<T, E> = { ok: true; value: T } | { ok: false; error: E };
- function loadConfig(): Result<Config, LoadError> { ... }
- const result = loadConfig(); if (!result.ok) { handleError(result.error); }

## Bad

- function loadConfig(): Config { throw new Error('failed'); }
- try { const cfg = loadConfig(); } catch { ... }
