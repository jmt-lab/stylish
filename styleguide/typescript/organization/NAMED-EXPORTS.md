---
type: Styleguide Rule
description: |-
  Use named exports to make imports explicit and enable better refactoring.
  Default exports hide the actual name and complicate tooling.
language: typescript
category: organization
rule_id: NAMED-EXPORTS
priority: warn
tags:
- exports
- refactoring
- clarity
---
Use named exports to make imports explicit and enable better refactoring.
Default exports hide the actual name and complicate tooling.

## Good

- export class UserService { }
// Import:
import { UserService } from './user-service';

## Bad

- export default class UserService { }
// Import:
import UserService from './user-service'; // Name not enforced
