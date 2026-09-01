---
type: Styleguide Rule
description: |-
  Each module/directory should have a clear responsibility. Internal
  implementation details should not leak across boundaries.
language: typescript
category: organization
rule_id: MODULE-BOUNDARIES
priority: warn
tags:
- modules
- encapsulation
- architecture
---
Each module/directory should have a clear responsibility. Internal
implementation details should not leak across boundaries.

## Good

- // auth/ exposes only AuthService via index.ts
// Internal helpers stay private

## Bad

- // Other modules importing auth/internal/jwt-helper.ts directly
