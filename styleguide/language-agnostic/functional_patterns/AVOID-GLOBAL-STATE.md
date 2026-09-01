---
type: Styleguide Rule
description: |-
  Global mutable state makes functions impure and code harder to test.
  Pass state explicitly through parameters instead.
language: language-agnostic
category: functional_patterns
rule_id: AVOID-GLOBAL-STATE
priority: error
tags:
- globals
- state
- testability
---
Global mutable state makes functions impure and code harder to test.
Pass state explicitly through parameters instead.

## Good

- void Update(GameState* state, float dt)

## Bad

- GameState g_state; // Global
void Update(float dt) { /* mutates global */ }
