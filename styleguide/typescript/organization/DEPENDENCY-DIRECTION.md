---
type: Styleguide Rule
description: |-
  Higher-level modules depend on lower-level modules, never the reverse.
  Core domain logic should not depend on infrastructure or UI.
language: typescript
category: organization
rule_id: DEPENDENCY-DIRECTION
priority: warn
tags:
- dependencies
- architecture
- layering
---
Higher-level modules depend on lower-level modules, never the reverse.
Core domain logic should not depend on infrastructure or UI.

## Good

- // UI -> Services -> Domain
// Infrastructure -> Domain

## Bad

- // Domain imports from UI
// Core imports from infrastructure
