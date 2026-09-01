---
type: Styleguide Rule
description: |-
  When some failures are acceptable, use Promise.allSettled instead of
  Promise.all. Makes failure handling explicit.
language: typescript
category: async
rule_id: PROMISE-ALLSETTLED-FOR-PARTIAL-FAILURE
priority: info
tags:
- errors
- promises
- resilience
---
When some failures are acceptable, use Promise.allSettled instead of
Promise.all. Makes failure handling explicit.

## Good

- const results = await Promise.allSettled([op1(), op2()]);
results.forEach(r => {
  if (r.status === 'fulfilled') use(r.value);
});

## Bad

- try {
  await Promise.all([op1(), op2()]);
} catch { ... } // Loses partial results
