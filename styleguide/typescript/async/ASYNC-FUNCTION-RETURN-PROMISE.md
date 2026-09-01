---
type: Styleguide Rule
description: |-
  Mark functions async only if they await. Otherwise return Promise directly.
  Async keyword adds overhead and hides synchronous execution.
language: typescript
category: async
rule_id: ASYNC-FUNCTION-RETURN-PROMISE
priority: info
tags:
- performance
- clarity
- async
---
Mark functions async only if they await. Otherwise return Promise directly.
Async keyword adds overhead and hides synchronous execution.

## Good

- // Preferred: return Promise directly without async overhead
function load(): Promise<Data> {
  return fetchData();
}
- // Acceptable: async when you need to await
async function load(): Promise<Data> {
  return await fetchData();
}

## Bad

- async function load() {
  return fetchData(); // Unnecessary async wrapper — not awaiting
}
