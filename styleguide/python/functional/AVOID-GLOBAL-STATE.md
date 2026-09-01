---
type: Styleguide Rule
description: |-
  Global mutable state makes functions impure and testing difficult.
  Pass state explicitly through parameters or use dependency injection.
language: python
category: functional
rule_id: AVOID-GLOBAL-STATE
priority: error
tags:
- globals
- state
- testability
---
Global mutable state makes functions impure and testing difficult.
Pass state explicitly through parameters or use dependency injection.

## Good

- def update(state: GameState, dt: float) -> GameState:
    return GameState(state.time + dt, state.score)

## Bad

- game_state = GameState()  # Global

def update(dt: float) -> None:
    game_state.time += dt
