---
type: Styleguide Rule
description: |-
  Don't translate constructs from C++, Java, C#, or Python one-to-one.
  Model errors with Result, resources with ownership and Drop, polymorphism
  with traits and enums, and absence with Option. Inheritance via Deref,
  Manager/Factory hierarchies, and throw_if_null helpers are smells.
language: rust
category: practices
rule_id: RUST-SHAPED-CODE
priority: warn
tags:
- practices
- idioms
- porting
- beautiful-rust
---
Don't translate constructs from C++, Java, C#, or Python one-to-one.
Model errors with Result, resources with ownership and Drop, polymorphism
with traits and enums, and absence with Option. Inheritance via Deref,
Manager/Factory hierarchies, and throw_if_null helpers are smells.

## Good

- pub enum Shape { Circle { radius: f64 }, Square { side: f64 } }

impl Shape {
    pub fn area(&self) -> f64 { ... }
}

## Bad

- pub trait IShape { fn area(&self) -> f64; }
pub struct ShapeFactory;
impl ShapeFactory { pub fn create(kind: &str) -> Option<Box<dyn IShape>> { ... } }
