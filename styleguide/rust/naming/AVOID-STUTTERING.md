---
type: Styleguide Rule
description: |-
  Don't repeat the module or type name in function/field names when
  the context is clear.
language: rust
category: naming
rule_id: AVOID-STUTTERING
priority: info
tags:
- naming
- clarity
- official
---
Don't repeat the module or type name in function/field names when
the context is clear.

## Good

- mod renderer;
impl Renderer { fn clear(&mut self) }
- struct Entity { health: f32 }

## Bad

- mod renderer;
impl Renderer { fn renderer_clear(&mut self) }
- struct Entity { entity_health: f32 }
