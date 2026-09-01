---
type: Styleguide Rule
description: |-
  Import types with 'import type' to make it clear they're compile-time only
  and enable better tree-shaking and dependency analysis.
language: typescript
category: organization
rule_id: TYPE-ONLY-IMPORTS
priority: info
tags:
- imports
- types
- optimization
---
Import types with 'import type' to make it clear they're compile-time only
and enable better tree-shaking and dependency analysis.

## Good

- import type { User } from './user';
import { createUser } from './user';

## Bad

- import { User, createUser } from './user'; // User is just a type
