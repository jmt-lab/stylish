---
type: Styleguide Rule
description: |-
  Every async operation must have error handling via try/catch or .catch().
  Unhandled rejections are invisible failure modes.
language: typescript
category: async
rule_id: HANDLE-PROMISE-REJECTIONS
priority: error
tags:
- errors
- promises
- safety
---
Every async operation must have error handling via try/catch or .catch().
Unhandled rejections are invisible failure modes.

## Good

- try {
  await fetchData();
} catch (err) {
  handleError(err);
}
- fetchData().catch(err => handleError(err));

## Bad

- await fetchData(); // No error handling
