---
type: Styleguide Rule
description: |-
  External async operations should have timeouts. Infinite waits are
  invisible hangs.
language: typescript
category: async
rule_id: TIMEOUT-HANDLING
priority: warn
tags:
- timeouts
- reliability
- errors
---
External async operations should have timeouts. Infinite waits are
invisible hangs.

## Good

- await Promise.race([
  fetchData(),
  timeout(5000)
]);
- const signal = AbortSignal.timeout(5000);
await fetch(url, { signal });

## Bad

- await fetchData(); // No timeout, could hang forever
