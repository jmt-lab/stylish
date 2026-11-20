---
type: Styleguide Rule
description: |-
  Choose every atomic Ordering deliberately and say why in a comment.
  Relaxed is enough for independent counters; publishing data to another
  thread needs a Release store paired with an Acquire load. Use SeqCst
  only when you need a single total order, and never as a substitute for
  reasoning. When unsure, use a Mutex.
language: rust
category: concurrency
rule_id: ATOMIC-ORDERING-DELIBERATE
priority: warn
tags:
- concurrency
- atomics
- memory-ordering
- rust-skills
---
Choose every atomic Ordering deliberately and say why in a comment.
Relaxed is enough for independent counters; publishing data to another
thread needs a Release store paired with an Acquire load. Use SeqCst
only when you need a single total order, and never as a substitute for
reasoning. When unsure, use a Mutex.

## Good

- // Relaxed: a statistics counter; nothing else is synchronized through it.
self.requests.fetch_add(1, Ordering::Relaxed);

// Release pairs with the Acquire load in `is_ready`, publishing `data`.
self.ready.store(true, Ordering::Release);

## Bad

- self.ready.store(true, Ordering::Relaxed); // reader may see ready without data
self.requests.fetch_add(1, Ordering::SeqCst); // SeqCst "to be safe"
