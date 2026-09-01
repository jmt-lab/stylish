---
type: Styleguide Rule
description: |-
  Use ?. for safe property access instead of manual null checks.
  More concise and handles undefined gracefully.
language: typescript
category: control_flow
rule_id: TS-OPTIONAL-CHAINING
priority: info
tags:
- optional-chaining
- null-safety
- conciseness
---
Use ?. for safe property access instead of manual null checks.
More concise and handles undefined gracefully.

## Good

- const name = user?.profile?.name;

## Bad

- const name = user && user.profile && user.profile.name;
