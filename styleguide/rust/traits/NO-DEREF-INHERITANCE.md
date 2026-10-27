---
type: Styleguide Rule
description: |-
  Implement Deref / DerefMut only for smart pointers and owning wrappers
  whose target is their borrowed view (Vec<T> to [T]). Never use Deref to fake
  inheritance from a "base" struct; write forwarding methods or a trait.
language: rust
category: traits
rule_id: NO-DEREF-INHERITANCE
priority: error
tags:
- traits
- deref
- anti-pattern
- beautiful-rust
---
Implement Deref / DerefMut only for smart pointers and owning wrappers
whose target is their borrowed view (Vec<T> to [T]). Never use Deref to fake
inheritance from a "base" struct; write forwarding methods or a trait.

## Good

- impl Deref for Utf8Buffer {
    type Target = str;
    fn deref(&self) -> &str { ... }
}
- impl Admin {
    pub fn name(&self) -> &str { self.user.name() }
}

## Bad

- impl Deref for Admin {
    type Target = User;
    fn deref(&self) -> &User { &self.user } // "Admin extends User"
}
