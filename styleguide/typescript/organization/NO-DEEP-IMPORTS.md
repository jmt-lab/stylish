---
type: Styleguide Rule
description: |-
  Import from the module's public API (index.ts), not from internal files.
  This respects encapsulation and allows internal refactoring.
language: typescript
category: organization
rule_id: NO-DEEP-IMPORTS
priority: warn
tags:
- imports
- encapsulation
- modularity
---
Import from the module's public API (index.ts), not from internal files.
This respects encapsulation and allows internal refactoring.

## Good

- import { UserService } from '@/user';

## Bad

- import { UserService } from '@/user/internal/services/user-service-impl';
