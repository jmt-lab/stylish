---
type: Styleguide Rule
description: |-
  Long-running async operations should accept AbortSignal for cancellation.
  Makes cancellation explicit and prevents resource leaks.
language: typescript
category: async
rule_id: ABORT-CONTROLLER-CANCELLATION
priority: warn
tags:
- cancellation
- resources
- cleanup
---
Long-running async operations should accept AbortSignal for cancellation.
Makes cancellation explicit and prevents resource leaks.

## Good

- async function fetch(url: string, signal: AbortSignal) {
  const response = await fetch(url, { signal });
}
- const controller = new AbortController();
fetchData(controller.signal);
controller.abort();

## Bad

- async function fetch(url: string) { ... } // No cancellation support
