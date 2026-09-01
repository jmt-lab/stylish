---
type: Styleguide Rule
description: |-
  Document why async operations are sequential or parallel. The choice
  affects both correctness and performance.
language: typescript
category: async
rule_id: SEQUENTIAL-VS-PARALLEL-EXPLICIT
priority: info
tags:
- documentation
- performance
- concurrency
---
Document why async operations are sequential or parallel. The choice
affects both correctness and performance.

## Good

- // Sequential: second depends on first
const user = await getUser();
const posts = await getPosts(user.id);
- // Parallel: independent operations
const [users, config] = await Promise.all([getUsers(), getConfig()]);

## Bad

- const a = await getA();
const b = await getB(); // Why sequential?
