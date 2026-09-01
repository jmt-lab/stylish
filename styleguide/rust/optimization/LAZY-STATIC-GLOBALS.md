---
type: Styleguide Rule
description: |-
  Global constants that require computation should use LazyLock
  (Rust 1.80+) for initialization on first access.
language: rust
category: optimization
rule_id: LAZY-STATIC-GLOBALS
priority: info
tags:
- optimization
- globals
- initialization
---
Global constants that require computation should use LazyLock
(Rust 1.80+) for initialization on first access.

## Good

- use std::sync::LazyLock;
static CONFIG: LazyLock<Config> = LazyLock::new(|| {
    Config::from_file("config.toml")
});

## Bad

- static mut CONFIG: Option<Config> = None; // Unsafe, awkward
