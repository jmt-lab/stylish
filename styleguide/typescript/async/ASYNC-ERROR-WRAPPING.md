---
type: Styleguide Rule
description: |-
  Catch and re-throw async errors with additional context. Async stack
  traces lose information across await boundaries.
language: typescript
category: async
rule_id: ASYNC-ERROR-WRAPPING
priority: warn
tags:
- errors
- debugging
- diagnostics
---
Catch and re-throw async errors with additional context. Async stack
traces lose information across await boundaries.

## Good

- try {
  await loadConfig();
} catch (err) {
  throw new Error(`Config load failed: ${err.message}`);
}

## Bad

- await loadConfig(); // Error has no context
