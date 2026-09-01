---
type: Styleguide Rule
description: |-
  Structure directories by feature or subsystem, not by technical type.
  This makes architectural boundaries visible and reduces cross-cutting dependencies.
language: typescript
category: organization
rule_id: FEATURE-DIRECTORIES
priority: warn
tags:
- directories
- architecture
- organization
---
Structure directories by feature or subsystem, not by technical type.
This makes architectural boundaries visible and reduces cross-cutting dependencies.

## Good

- auth/ - Authentication subsystem
user/ - User management
product/ - Product domain

## Bad

- models/ - All models
controllers/ - All controllers
views/ - All views
