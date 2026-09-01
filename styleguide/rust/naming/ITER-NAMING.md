---
type: Styleguide Rule
description: 'Use standard names for iterator methods: iter(), iter_mut(), into_iter().'
language: rust
category: naming
rule_id: ITER-NAMING
priority: error
tags:
- naming
- iterators
- official
---
Use standard names for iterator methods: iter(), iter_mut(), into_iter().

## Good

- fn iter(&self) -> Iter<T>
- fn iter_mut(&mut self) -> IterMut<T>
- fn into_iter(self) -> IntoIter<T>

## Bad

- fn iterator(&self) -> Iter<T>
- fn get_iter(&self) -> Iter<T>
