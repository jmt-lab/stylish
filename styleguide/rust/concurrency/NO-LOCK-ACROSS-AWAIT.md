---
type: Styleguide Rule
description: |-
  Don't hold a std::sync::MutexGuard (or RefCell borrow) across an .await.
  It makes the future !Send and can deadlock the executor. Drop the guard
  before awaiting, or use an async-aware lock when you must hold it.
language: rust
category: concurrency
rule_id: NO-LOCK-ACROSS-AWAIT
priority: error
tags:
- concurrency
- async
- mutex
- beautiful-rust
---
Don't hold a std::sync::MutexGuard (or RefCell borrow) across an .await.
It makes the future !Send and can deadlock the executor. Drop the guard
before awaiting, or use an async-aware lock when you must hold it.

## Good

- let request = {
    let mut queue = self.queue.lock().expect("queue mutex poisoned");
    queue.pop_front()
};
if let Some(request) = request { send(request).await?; }

## Bad

- let mut queue = self.queue.lock().expect("queue mutex poisoned");
if let Some(request) = queue.pop_front() {
    send(request).await?; // guard held across await
}
