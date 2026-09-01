---
type: Styleguide Rule
description: |-
  Use proper logging library. Enable no-console ESLint rule.
  Console statements leak information and clutter output.
language: typescript
category: practices
rule_id: NO-CONSOLE-PRODUCTION
priority: warn
tags:
- logging
- production
- debugging
---
Use proper logging library. Enable no-console ESLint rule.
Console statements leak information and clutter output.

## Good

- logger.info('Processing', {userId});

## Bad

- console.log('user:', user); // In production code
