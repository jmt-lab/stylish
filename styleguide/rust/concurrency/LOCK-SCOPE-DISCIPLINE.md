---
type: Styleguide Rule
description: |-
  Keep data with linked invariants under one lock, keep lock scopes to a
  few lines, never call user closures or callbacks while holding a lock, and
  never return a MutexGuard from a public method.
language: rust
category: concurrency
rule_id: LOCK-SCOPE-DISCIPLINE
priority: warn
tags:
- concurrency
- mutex
- deadlock
- beautiful-rust
---
Keep data with linked invariants under one lock, keep lock scopes to a
few lines, never call user closures or callbacks while holding a lock, and
never return a MutexGuard from a public method.

## Good

- let snapshot = {
    let state = self.state.lock().expect("state mutex poisoned");
    state.pending.clone()
};
for job in snapshot { (self.on_job)(job); }

## Bad

- let state = self.state.lock().expect("state mutex poisoned");
for job in &state.pending { (self.on_job)(job.clone()); } // callback may re-lock: deadlock
- pub fn state(&self) -> MutexGuard<'_, State> { ... }
