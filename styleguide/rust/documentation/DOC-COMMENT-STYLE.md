---
type: Styleguide Rule
description: Use /// for doc comments instead of /** ... */.
language: rust
category: documentation
rule_id: DOC-COMMENT-STYLE
priority: warn
tags:
- documentation
- comments
- official
---
Use /// for doc comments instead of /** ... */.

## Good

- /// Renders the scene with the given configuration.
fn render_scene(&self, config: &Config)

## Bad

- /** Renders the scene */
