---
type: Styleguide Rule
description: |-
  Complex boolean flags make control flow hard to follow.
  Use enums to represent state explicitly.
language: rust
category: control_flow
rule_id: AVOID-BOOL-FLAGS
priority: warn
tags:
- control-flow
- state
- clarity
- carmack
---
Complex boolean flags make control flow hard to follow.
Use enums to represent state explicitly.

## Good

- enum State { Init, Running, Paused, Stopped }
match state { ... }

## Bad

- let running = true;
let paused = false;
let stopped = false;
if running && !paused && !stopped { ... }
