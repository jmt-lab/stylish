---
type: Styleguide Rule
description: |-
  Decide early whether a trait will be used as dyn Trait. Generic methods
  and Self outside the receiver break object safety; exclude such methods with
  where Self: Sized so the rest of the trait stays dyn-compatible.
language: rust
category: traits
rule_id: DECIDE-OBJECT-SAFETY-EARLY
priority: info
tags:
- traits
- dyn
- object-safety
- beautiful-rust
---
Decide early whether a trait will be used as dyn Trait. Generic methods
and Self outside the receiver break object safety; exclude such methods with
where Self: Sized so the rest of the trait stays dyn-compatible.

## Good

- pub trait Sink {
    fn write(&mut self, record: &Record);
    fn write_all<I: IntoIterator<Item = Record>>(&mut self, records: I) where Self: Sized { ... }
}

## Bad

- pub trait Sink {
    fn write(&mut self, record: &Record);
    fn write_all<I: IntoIterator<Item = Record>>(&mut self, records: I); // Box<dyn Sink> no longer compiles
}
