---
type: Styleguide Rule
description: |-
  To move a value out of a &mut place, swap in a placeholder with
  std::mem::take (needs Default), std::mem::replace, or Option::take instead
  of cloning it.
language: rust
category: ownership
rule_id: MEM-TAKE-OVER-CLONE
priority: warn
tags:
- ownership
- borrowing
- clone
- mem
- beautiful-rust
---
To move a value out of a &mut place, swap in a placeholder with
std::mem::take (needs Default), std::mem::replace, or Option::take instead
of cloning it.

## Good

- fn promote(state: &mut State) {
    if let State::Pending { name } = state {
        *state = State::Active { name: mem::take(name) };
    }
}
- let batch = mem::take(&mut self.buffer);

## Bad

- fn promote(state: &mut State) {
    if let State::Pending { name } = state {
        *state = State::Active { name: name.clone() };
    }
}
- let batch = self.buffer.clone();
self.buffer.clear();
