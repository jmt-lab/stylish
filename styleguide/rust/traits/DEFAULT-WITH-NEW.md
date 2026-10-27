---
type: Styleguide Rule
description: |-
  Implement Default for types that have an argument-less new() or
  otherwise have a natural default state (Clippy: new_without_default).
language: rust
category: traits
rule_id: DEFAULT-WITH-NEW
priority: warn
tags:
- traits
- default
- constructors
- clippy
- google-style
---
Implement Default for types that have an argument-less new() or
otherwise have a natural default state (Clippy: new_without_default).

## Good

- #[derive(Default)]
pub struct Registry { entries: HashMap<String, Entry> }

impl Registry {
    pub fn new() -> Self { Self::default() }
}

## Bad

- pub struct Registry { entries: HashMap<String, Entry> }

impl Registry {
    pub fn new() -> Self { Self { entries: HashMap::new() } }
} // unusable with unwrap_or_default(), mem::take(), #[derive(Default)] parents
