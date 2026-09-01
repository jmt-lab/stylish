---
type: Styleguide Rule
description: |-
  Group imports in consistent order: external packages, internal absolute paths,
  relative imports. Separate groups with blank lines. Makes dependencies visible.
language: typescript
category: organization
rule_id: IMPORT-ORDERING
priority: info
tags:
- imports
- formatting
- dependencies
---
Group imports in consistent order: external packages, internal absolute paths,
relative imports. Separate groups with blank lines. Makes dependencies visible.

## Good

- import { Observable } from 'rxjs';

import { UserService } from '@/services';

import { validate } from './validation';

## Bad

- import { validate } from './validation';
import { UserService } from '@/services';
import { Observable } from 'rxjs';
