---
type: Styleguide Rule
description: |-
  Create index.ts files to expose the public API of a module/directory.
  This creates a clear boundary between public and internal code.
language: typescript
category: organization
rule_id: BARREL-EXPORTS
priority: info
tags:
- modules
- encapsulation
- api
---
Create index.ts files to expose the public API of a module/directory.
This creates a clear boundary between public and internal code.

## Good

- // auth/index.ts
export { AuthService } from './auth-service';
export type { AuthConfig } from './types';

## Bad

- // Importing internal implementation
import { AuthService } from './auth/internal/auth-service-impl';
