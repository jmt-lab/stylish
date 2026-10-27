---
type: Styleguide Rule
description: |-
  Long CPU-bound work in async code must yield periodically (roughly every
  10-100 microseconds of work) or move to spawn_blocking, so it doesn't starve
  other tasks on the executor.
language: rust
category: concurrency
rule_id: YIELD-IN-CPU-BOUND-ASYNC
priority: warn
tags:
- concurrency
- async
- performance
- beautiful-rust
---
Long CPU-bound work in async code must yield periodically (roughly every
10-100 microseconds of work) or move to spawn_blocking, so it doesn't starve
other tasks on the executor.

## Good

- let digest = tokio::task::spawn_blocking(move || sha256(&large_file)).await?;
- for (i, chunk) in chunks.iter().enumerate() {
    process(chunk);
    if i % 64 == 0 { tokio::task::yield_now().await; }
}

## Bad

- async fn index(docs: Vec<Doc>) { for doc in docs { tokenize(&doc); } } // blocks the worker thread
