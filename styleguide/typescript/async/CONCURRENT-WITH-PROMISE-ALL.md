---
type: Styleguide Rule
description: |-
  When operations can run concurrently, use Promise.all to make parallelism
  explicit. Sequential awaits hide performance opportunities.
language: typescript
category: async
rule_id: CONCURRENT-WITH-PROMISE-ALL
priority: warn
tags:
- performance
- concurrency
- promises
---
When operations can run concurrently, use Promise.all to make parallelism
explicit. Sequential awaits hide performance opportunities.

## Good

- const [users, posts] = await Promise.all([getUsers(), getPosts()]);

## Bad

- const users = await getUsers();
const posts = await getPosts(); // Sequential when could be parallel
