---
type: Styleguide Rule
description: |-
  Never use static mut. References to it are denied in Rust 2024, and
  every access is a potential data race. Use an atomic, a Mutex or
  OnceLock in a static, or thread_local! with Cell or RefCell for
  per-thread state.
language: rust
category: safety
rule_id: NO-STATIC-MUT
priority: error
tags:
- unsafe
- globals
- edition-2024
- concurrency
- rust-skills
---
Never use static mut. References to it are denied in Rust 2024, and
every access is a potential data race. Use an atomic, a Mutex or
OnceLock in a static, or thread_local! with Cell or RefCell for
per-thread state.

## Good

- static REQUEST_COUNT: AtomicU64 = AtomicU64::new(0);

thread_local! {
    static SCRATCH: RefCell<Vec<u8>> = const { RefCell::new(Vec::new()) };
}

## Bad

- static mut REQUEST_COUNT: u64 = 0;

unsafe { REQUEST_COUNT += 1; } // data race when called from two threads
