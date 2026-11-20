---
type: Styleguide Rule
description: |-
  In edition 2024 (Rust 1.88+), combine pattern bindings and boolean
  conditions in one if or while with let chains instead of nesting if let
  blocks. When every branch is a pattern on the same values, a match is
  still clearer (MATCH-OVER-IF-LET-CHAIN).
language: rust
category: control_flow
rule_id: LET-CHAINS
priority: info
tags:
- control-flow
- pattern-matching
- edition-2024
- rust-skills
---
In edition 2024 (Rust 1.88+), combine pattern bindings and boolean
conditions in one if or while with let chains instead of nesting if let
blocks. When every branch is a pattern on the same values, a match is
still clearer (MATCH-OVER-IF-LET-CHAIN).

## Good

- if let Some(user) = session.user()
    && user.is_admin()
    && let Some(target) = request.target()
{
    grant(user, target);
}

## Bad

- if let Some(user) = session.user() {
    if user.is_admin() {
        if let Some(target) = request.target() {
            grant(user, target);
        }
    }
}
