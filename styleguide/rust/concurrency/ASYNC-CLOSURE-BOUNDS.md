---
type: Styleguide Rule
description: |-
  Accept async callbacks with AsyncFn, AsyncFnMut, or AsyncFnOnce bounds
  (stable since Rust 1.85) instead of the two-parameter F: Fn() -> Fut,
  Fut: Future pattern. The new bounds let the returned future borrow from
  the closure's captures and read more clearly.
language: rust
category: concurrency
rule_id: ASYNC-CLOSURE-BOUNDS
priority: info
tags:
- concurrency
- async
- closures
- rust-skills
---
Accept async callbacks with AsyncFn, AsyncFnMut, or AsyncFnOnce bounds
(stable since Rust 1.85) instead of the two-parameter F: Fn() -> Fut,
Fut: Future pattern. The new bounds let the returned future borrow from
the closure's captures and read more clearly.

## Good

- async fn with_retry<T>(attempts: u32, operation: impl AsyncFn() -> Result<T, Error>) -> Result<T, Error> {
    // ...
}

## Bad

- async fn with_retry<T, F, Fut>(attempts: u32, operation: F) -> Result<T, Error>
where
    F: Fn() -> Fut,
    Fut: Future<Output = Result<T, Error>>,
{
    // ...
}
