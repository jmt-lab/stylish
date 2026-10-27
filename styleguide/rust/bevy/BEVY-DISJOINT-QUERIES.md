---
type: Styleguide Rule
description: |-
  Two parameters of one Bevy system that can reach the same component
  mutably compile but panic (B0001) on first run; Res<T> beside ResMut<T>
  panics too (B0002). Make queries disjoint with Without filters matching
  the game's rules, or use a ParamSet when they genuinely overlap.
language: rust
category: bevy
rule_id: BEVY-DISJOINT-QUERIES
priority: error
tags:
- bevy
- ecs
- queries
- correctness
- beautiful-rust
---
Two parameters of one Bevy system that can reach the same component
mutably compile but panic (B0001) on first run; Res<T> beside ResMut<T>
panics too (B0002). Make queries disjoint with Without filters matching
the game's rules, or use a ParamSet when they genuinely overlap.

## Good

- fn apply_hits(
    mut players: Query<&mut Health, (With<Player>, Without<Enemy>)>,
    mut enemies: Query<&mut Health, (With<Enemy>, Without<Player>)>,
) { ... }

## Bad

- fn apply_hits(
    mut players: Query<&mut Health, With<Player>>,
    mut enemies: Query<&mut Health, With<Enemy>>, // B0001 panic on first frame
) { ... }
