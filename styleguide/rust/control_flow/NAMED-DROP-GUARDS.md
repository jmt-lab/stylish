---
type: Styleguide Rule
description: |-
  Bind RAII guards to a named variable (let _guard = ...) so they live
  until the end of the scope. let _ = ... drops the value immediately, which
  silently releases locks or runs cleanup too early.
language: rust
category: control_flow
rule_id: NAMED-DROP-GUARDS
priority: error
tags:
- control-flow
- raii
- drop
- beautiful-rust
---
Bind RAII guards to a named variable (let _guard = ...) so they live
until the end of the scope. let _ = ... drops the value immediately, which
silently releases locks or runs cleanup too early.

## Good

- let _lock = state.lock().expect("state mutex poisoned");
let _span = tracing::info_span!("sync").entered();

## Bad

- let _ = state.lock().expect("state mutex poisoned"); // unlocked on this line
let _ = tracing::info_span!("sync").entered(); // span exits immediately
