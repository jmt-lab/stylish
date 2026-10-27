---
type: Styleguide Rule
description: |-
  Reusable library code that only needs to iterate over its input should
  accept impl IntoIterator (or a generic iterator) instead of a slice or Vec.
  This lets callers pass any collection or iterator chain without copying.
  Application code may accept &[T] when it is simpler.
language: rust
category: api_design
rule_id: ACCEPT-INTOITERATOR-IN-LIBRARIES
priority: info
tags:
- api-design
- iterators
- libraries
- parameters
- google-style
---
Reusable library code that only needs to iterate over its input should
accept impl IntoIterator (or a generic iterator) instead of a slice or Vec.
This lets callers pass any collection or iterator chain without copying.
Application code may accept &[T] when it is simpler.

## Good

- pub fn sum_sizes(files: impl IntoIterator<Item = FileInfo>) -> u64 {
    files.into_iter().map(|file| file.size).sum()
}

## Bad

- pub fn sum_sizes(files: Vec<FileInfo>) -> u64 {
    files.iter().map(|file| file.size).sum()
} // callers with an iterator must collect first
