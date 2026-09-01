---
type: Styleguide Rule
description: |-
  Avoid deep nesting (more than 3 levels). Flat structure is easier
  to navigate and refactor.
language: rust
category: organization
rule_id: FLAT-OVER-DEEP
priority: info
tags:
- organization
- structure
- carmack
---
Avoid deep nesting (more than 3 levels). Flat structure is easier
to navigate and refactor.

## Good

- src/
  renderer/
  audio/
  game/

## Bad

- src/
  systems/
    graphics/
      rendering/
        backend/
          vulkan/
