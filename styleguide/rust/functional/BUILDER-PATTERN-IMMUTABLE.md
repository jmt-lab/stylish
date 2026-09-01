---
type: Styleguide Rule
description: |-
  Complex object construction should use builder pattern for
  immutable, readable initialization.
language: rust
category: functional
rule_id: BUILDER-PATTERN-IMMUTABLE
priority: info
tags:
- functional
- builder
- construction
---
Complex object construction should use builder pattern for
immutable, readable initialization.

## Good

- let config = ConfigBuilder::new()
    .with_width(1920)
    .with_height(1080)
    .with_vsync(true)
    .build();

## Bad

- let mut config = Config::default();
config.width = 1920;
config.height = 1080;
config.vsync = true;
