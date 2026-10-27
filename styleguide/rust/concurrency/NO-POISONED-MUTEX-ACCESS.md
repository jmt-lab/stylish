---
type: Styleguide Rule
description: |-
  Never reach inside a poisoned mutex (e.g. via PoisonError::into_inner),
  no matter how tempting. Poisoning means another thread panicked mid-update
  and the protected data may violate its invariants.
language: rust
category: concurrency
rule_id: NO-POISONED-MUTEX-ACCESS
priority: error
tags:
- concurrency
- mutex
- poison
- safety
- google-style
---
Never reach inside a poisoned mutex (e.g. via PoisonError::into_inner),
no matter how tempting. Poisoning means another thread panicked mid-update
and the protected data may violate its invariants.

## Good

- let guard = state.lock().expect("state mutex poisoned: a writer panicked");
- let guard = state.lock().map_err(|_| StatePoisonedSnafu.build())?;

## Bad

- let guard = state.lock().unwrap_or_else(|poisoned| poisoned.into_inner());
- let guard = match state.lock() { Ok(g) => g, Err(e) => e.into_inner() };
