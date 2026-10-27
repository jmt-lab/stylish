---
type: Styleguide Rule
description: |-
  Don't unwrap Query::single() or Query::get(); they fail when the entity
  count changes (the player dies, a second camera spawns). Use Single<D, F>,
  let Ok(..) = .. else { return };, or return Result from the system. Use
  try_insert / try_despawn for entities that may already be gone.
language: rust
category: bevy
rule_id: BEVY-NO-UNWRAP-QUERIES
priority: error
tags:
- bevy
- ecs
- panics
- queries
- beautiful-rust
---
Don't unwrap Query::single() or Query::get(); they fail when the entity
count changes (the player dies, a second camera spawns). Use Single<D, F>,
let Ok(..) = .. else { return };, or return Result from the system. Use
try_insert / try_despawn for entities that may already be gone.

## Good

- fn follow_player(player: Single<&Transform, With<Player>>, mut camera: Single<&mut Transform, With<Camera>>) { ... }
- commands.entity(enemy).try_despawn();

## Bad

- fn follow_player(players: Query<&Transform, With<Player>>) {
    let player = players.single().unwrap(); // crashes once the player despawns
}
