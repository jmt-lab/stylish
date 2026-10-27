---
type: Styleguide Rule
description: |-
  If a fallible function takes ownership of an argument, return it inside
  the error so the caller can recover or retry without cloning beforehand
  (as String::from_utf8 does with FromUtf8Error::into_bytes).
language: rust
category: api_design
rule_id: RETURN-CONSUMED-ARG-ON-ERROR
priority: info
tags:
- api-design
- errors
- ownership
- beautiful-rust
---
If a fallible function takes ownership of an argument, return it inside
the error so the caller can recover or retry without cloning beforehand
(as String::from_utf8 does with FromUtf8Error::into_bytes).

## Good

- #[derive(Debug, Snafu)]
#[snafu(display("queue is full"))]
pub struct QueueFullError<T> { item: T }

impl<T> QueueFullError<T> {
    pub fn into_item(self) -> T { self.item }
}

pub fn push(&mut self, item: T) -> Result<(), QueueFullError<T>> { ... }

## Bad

- pub fn push(&mut self, item: T) -> Result<(), QueueFullError> { ... }
// item is dropped on failure; callers must clone before every push
