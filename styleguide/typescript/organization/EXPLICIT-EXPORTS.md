---
type: Styleguide Rule
description: |-
  Explicitly list exports rather than using export *. This makes the public
  API visible and prevents accidental exposure of internal code.
language: typescript
category: organization
rule_id: EXPLICIT-EXPORTS
priority: warn
tags:
- exports
- encapsulation
- api
---
Explicitly list exports rather than using export *. This makes the public
API visible and prevents accidental exposure of internal code.

## Good

- export { UserService } from './user-service';
export { AuthService } from './auth-service';

## Bad

- export * from './user-service'; // Exposes everything
