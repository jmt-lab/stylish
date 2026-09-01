---
type: Styleguide Rule
description: |-
  Rather than mutating, create new values with struct update syntax.
  This makes data flow clear.
language: rust
category: functional
rule_id: IMMUTABLE-UPDATE
priority: info
tags:
- functional
- immutability
- carmack
---
Rather than mutating, create new values with struct update syntax.
This makes data flow clear.

## Good

- let updated = Player {
    health: player.health - damage,
    last_hit: now,
    ..player
};

## Bad

- player.health -= damage;
player.last_hit = now;
// Mutation hides data flow
