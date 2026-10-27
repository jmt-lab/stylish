---
type: Styleguide Rule
description: |-
  In Bevy systems, take system parameters (Res, ResMut, Query, Single,
  Commands, Local, MessageReader/Writer) by value; they are already borrows
  Bevy builds for one run. Don't change them to references or flag them as
  needless pass-by-value. Inside systems, helpers still take plain borrows.
language: rust
category: bevy
rule_id: BEVY-SYSTEM-PARAMS-BY-VALUE
priority: warn
tags:
- bevy
- ecs
- systems
- framework
- beautiful-rust
---
In Bevy systems, take system parameters (Res, ResMut, Query, Single,
Commands, Local, MessageReader/Writer) by value; they are already borrows
Bevy builds for one run. Don't change them to references or flag them as
needless pass-by-value. Inside systems, helpers still take plain borrows.

## Good

- fn apply_damage(mut query: Query<&mut Health>, time: Res<Time>) {
    for mut health in &mut query { decay(&mut health, time.delta_secs()); }
}

## Bad

- fn apply_damage(query: &mut Query<&mut Health>, time: &Res<Time>) { ... } // not a valid system
