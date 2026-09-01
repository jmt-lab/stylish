---
type: Styleguide Rule
description: |-
  File names should use snake_case and match their module name.
  Each module should be in its own file or directory.
language: rust
category: organization
rule_id: FILE-MATCHES-MODULE
priority: error
tags:
- organization
- files
- official
---
File names should use snake_case and match their module name.
Each module should be in its own file or directory.

## Good

- entity_manager.rs → mod entity_manager
- render_system.rs → mod render_system

## Bad

- EntityManager.rs // Wrong case
- rendersystem.rs // Missing underscore
