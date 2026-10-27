---
type: Styleguide Rule
description: |-
  In Bevy crates, use bevy::prelude::* (Bevy's documented import), and let
  plain-data components and resources have public fields (Health(pub u32)).
  Keep fields private only when they must hold an invariant together. Allow
  clippy::type_complexity, too_many_arguments, and needless_pass_by_value
  instead of splitting systems to silence them.
language: rust
category: bevy
rule_id: BEVY-PRELUDE-AND-PLAIN-DATA
priority: info
tags:
- bevy
- imports
- components
- framework
- beautiful-rust
---
In Bevy crates, use bevy::prelude::* (Bevy's documented import), and let
plain-data components and resources have public fields (Health(pub u32)).
Keep fields private only when they must hold an invariant together. Allow
clippy::type_complexity, too_many_arguments, and needless_pass_by_value
instead of splitting systems to silence them.

## Good

- use bevy::prelude::*;

#[derive(Component)]
pub struct Velocity(pub Vec2);

## Bad

- use bevy::ecs::system::{Query, Res};
use bevy::time::Time; // fighting the framework's import convention

#[derive(Component)]
pub struct Velocity(Vec2);
impl Velocity { pub fn new(v: Vec2) -> Self { ... } pub fn get(&self) -> Vec2 { ... } }
