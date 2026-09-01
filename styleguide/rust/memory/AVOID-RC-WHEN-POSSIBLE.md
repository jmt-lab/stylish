---
type: Styleguide Rule
description: |-
  Reference counting has runtime overhead. Use only when multiple
  owners truly need shared ownership. Shared ownership is justified
  when multiple independent owners need to outlive each other with
  no clear single owner.
language: rust
category: memory
rule_id: AVOID-RC-WHEN-POSSIBLE
priority: warn
tags:
- memory
- ownership
- performance
---
Reference counting has runtime overhead. Use only when multiple
owners truly need shared ownership. Shared ownership is justified
when multiple independent owners need to outlive each other with
no clear single owner.

## Good

- // Clear ownership
struct Game {
    entities: Vec<Entity>, // Game owns entities
}

## Bad

- // Unnecessary shared ownership
struct Game {
    entities: Vec<Rc<Entity>>, // Why shared?
}
