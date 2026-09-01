---
type: Styleguide Rule
description: |-
  Invalid state indicates programmer error — throw immediately rather than
  trying to recover or continue with corrupted state. Exceptions should
  indicate contract violations and invalid state, not expected failures.
  These are like assertions.
language: typescript
category: error_handling
rule_id: FAIL-FAST
priority: error
tags:
- fail-fast
- correctness
- safety
- exceptions
- programmer-errors
- contracts
---
Invalid state indicates programmer error — throw immediately rather than
trying to recover or continue with corrupted state. Exceptions should
indicate contract violations and invalid state, not expected failures.
These are like assertions.

## Good

- if (!this.initialized) throw new Error('must call init() first');
- console.assert(this.invariant(), 'invariant violated');
- if (index < 0 || index >= arr.length) throw new Error('index out of bounds');

## Bad

- if (!this.initialized) { this.init(); } // Hiding bug
- if (!fileExists(path)) throw new Error('file not found'); // Expected failure — use Result
