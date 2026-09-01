---
type: Styleguide Rule
description: |-
  Use async/await instead of .then() chains. Async/await makes control flow
  explicit and sequential, matching synchronous code structure.
language: typescript
category: async
rule_id: ASYNC-AWAIT-OVER-THEN
priority: warn
tags:
- async
- readability
- control-flow
---
Use async/await instead of .then() chains. Async/await makes control flow
explicit and sequential, matching synchronous code structure.

## Good

- const data = await fetchData();
const result = await process(data);
- async function load() {
  const user = await getUser();
  return user;
}

## Bad

- fetchData().then(data => process(data)).then(result => ...);
