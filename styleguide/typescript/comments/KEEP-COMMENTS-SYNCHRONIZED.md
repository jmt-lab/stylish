---
type: Styleguide Rule
description: |-
  When code changes, update comments. Stale comments mislead readers
  and are worse than no comments.
language: typescript
category: comments
rule_id: KEEP-COMMENTS-SYNCHRONIZED
priority: error
tags:
- maintenance
- accuracy
- hygiene
---
When code changes, update comments. Stale comments mislead readers
and are worse than no comments.

## Bad

- // Returns boolean return entity; // Actually returns entity object
