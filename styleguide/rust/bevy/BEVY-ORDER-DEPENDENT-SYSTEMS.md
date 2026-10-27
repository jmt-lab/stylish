---
type: Styleguide Rule
description: |-
  Bevy systems added together have no order unless you give one. If a
  system reads what another writes in the same frame (resource, message,
  component, or Commands spawns/despawns, which are deferred until a sync
  point), order them with .chain(), .before()/.after(), or system sets.
language: rust
category: bevy
rule_id: BEVY-ORDER-DEPENDENT-SYSTEMS
priority: error
tags:
- bevy
- ecs
- scheduling
- correctness
- beautiful-rust
---
Bevy systems added together have no order unless you give one. If a
system reads what another writes in the same frame (resource, message,
component, or Commands spawns/despawns, which are deferred until a sync
point), order them with .chain(), .before()/.after(), or system sets.

## Good

- app.add_systems(Update, (spawn_wave, check_wave_cleared).chain());

## Bad

- app.add_systems(Update, (spawn_wave, check_wave_cleared));
// check_wave_cleared may run before spawns apply, see zero enemies, and start a second wave
