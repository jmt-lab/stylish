---
type: Styleguide Rule
description: |-
  Structs with all-public fields used primarily as a "bag of options" for
  a function should implement Default, so callers can use struct update
  syntax and set only what they care about.
language: rust
category: traits
rule_id: OPTIONS-STRUCT-DEFAULT
priority: warn
tags:
- traits
- default
- configuration
- google-style
---
Structs with all-public fields used primarily as a "bag of options" for
a function should implement Default, so callers can use struct update
syntax and set only what they care about.

## Good

- #[derive(Debug, Default)]
pub struct RenderOptions {
    pub width: Option<u32>,
    pub dark_mode: bool,
    pub line_numbers: bool,
}

render(&doc, RenderOptions { dark_mode: true, ..Default::default() });

## Bad

- pub struct RenderOptions {
    pub width: Option<u32>,
    pub dark_mode: bool,
    pub line_numbers: bool,
}

render(&doc, RenderOptions { width: None, dark_mode: true, line_numbers: false });
