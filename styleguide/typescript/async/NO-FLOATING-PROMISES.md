---
type: Styleguide Rule
description: |-
  Every Promise must be awaited or explicitly voided. Floating promises
  hide errors and create invisible state transitions.
language: typescript
category: async
rule_id: NO-FLOATING-PROMISES
priority: error
tags:
- promises
- errors
- safety
---
Every Promise must be awaited or explicitly voided. Floating promises
hide errors and create invisible state transitions.

## Good

- await saveData(data);
- void saveData(data); // Explicitly fire-and-forget

## Bad

- saveData(data); // Floating promise
