---
type: Styleguide Rule
description: |-
  Global mutable state makes functions impure and code untestable.
  Pass state explicitly through parameters or use dependency injection.
language: typescript
category: functional
rule_id: NO-GLOBAL-STATE
priority: error
tags:
- globals
- state
- testability
---
Global mutable state makes functions impure and code untestable.
Pass state explicitly through parameters or use dependency injection.

## Good

- function update(state: GameState, dt: number): GameState

## Bad

- let globalState: GameState;
function update(dt: number): void {
  globalState = ...
}
