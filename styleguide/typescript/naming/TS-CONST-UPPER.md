---
type: Styleguide Rule
description: |-
  Module-level constants use SCREAMING_SNAKE_CASE. Enum members use
  PascalCase (see TS-ENUM-PASCAL). Aligns with Carmack's CONST-NAMING
  principle.
language: typescript
category: naming
rule_id: TS-CONST-UPPER
priority: warn
tags:
- constants
- conventions
---
Module-level constants use SCREAMING_SNAKE_CASE. Enum members use
PascalCase (see TS-ENUM-PASCAL). Aligns with Carmack's CONST-NAMING
principle.

## Good

- const MAX_ENTITIES = 1024;
- const DEFAULT_TIMEOUT_MS = 5000;
- export const API_VERSION = '1.0';

## Bad

- const maxEntities = 1024; // camelCase for constant
- const defaultTimeoutMs = 5000; // camelCase
- enum Status { ACTIVE, INACTIVE } // Use PascalCase for enum members
