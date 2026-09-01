---
type: Styleguide Rule
description: |-
  Build complex operations by composing small, pure closures.
  Each closure does one thing.
language: rust
category: functional
rule_id: CLOSURE-COMPOSITION
priority: info
tags:
- functional
- closures
- composition
---
Build complex operations by composing small, pure closures.
Each closure does one thing.

## Good

- let transform = |v: Vec3| v.normalized();
let scale = |v: Vec3| v * 2.0;
let result = entities.iter()
    .map(|e| e.position)
    .map(transform)
    .map(scale);

## Bad

- let result = entities.iter()
    .map(|e| {
        let v = e.position;
        let norm = v.normalized();
        norm * 2.0
    });
