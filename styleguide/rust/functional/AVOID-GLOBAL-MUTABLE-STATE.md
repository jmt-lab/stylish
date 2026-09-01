---
type: Styleguide Rule
description: |-
  Carmack principle: Global mutable state makes functions impure.
  Pass state explicitly through parameters.
language: rust
category: functional
rule_id: AVOID-GLOBAL-MUTABLE-STATE
priority: error
tags:
- functional
- state
- globals
- carmack
---
Carmack principle: Global mutable state makes functions impure.
Pass state explicitly through parameters.

## Good

- fn update(state: &mut GameState, dt: f32) { ... }

## Bad

- static mut GAME_STATE: GameState = ...;
fn update(dt: f32) {
    unsafe { GAME_STATE.update(dt); }
}
