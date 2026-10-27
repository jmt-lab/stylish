---
type: Styleguide Rule
description: |-
  Custom collections implement FromIterator and Extend, IntoIterator for
  the owned and borrowed forms, and iter()/iter_mut() returning types named
  Iter/IterMut/IntoIter. Add DoubleEndedIterator / ExactSizeIterator where
  applicable and keep size_hint truthful.
language: rust
category: traits
rule_id: COLLECTION-TRAITS
priority: info
tags:
- traits
- collections
- iterators
- beautiful-rust
---
Custom collections implement FromIterator and Extend, IntoIterator for
the owned and borrowed forms, and iter()/iter_mut() returning types named
Iter/IterMut/IntoIter. Add DoubleEndedIterator / ExactSizeIterator where
applicable and keep size_hint truthful.

## Good

- impl<T> FromIterator<T> for Ring<T> { ... }
impl<T> Extend<T> for Ring<T> { ... }
impl<T> IntoIterator for Ring<T> { type IntoIter = IntoIter<T>; ... }
impl<'a, T> IntoIterator for &'a Ring<T> { type IntoIter = Iter<'a, T>; ... }

## Bad

- impl<T> Ring<T> {
    pub fn to_vec(&self) -> Vec<T> { ... } // only way to iterate; collect() unsupported
}
