---
type: Styleguide Rule
description: |-
  Each module should depend on as few other modules as possible.
  Excessive dependencies indicate tight coupling and poor boundaries.
language: typescript
category: organization
rule_id: MINIMIZE-DEPENDENCIES
priority: warn
tags:
- dependencies
- coupling
- modularity
---
Each module should depend on as few other modules as possible.
Excessive dependencies indicate tight coupling and poor boundaries.

## Good

- // 2-3 focused imports
import { User } from './user';
import { validate } from './validation';

## Bad

- // 15+ imports from all over
import { A, B, C, D, E, F, G, H, I, J, K, L, M, N, O } from '...';
