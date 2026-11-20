---
type: Styleguide Rule
description: |-
  Give long-running tasks an explicit shutdown signal, such as
  tokio_util's CancellationToken or a watch channel. Select on it in their
  loops, then wait for them to finish before main returns. Dropping the
  runtime kills tasks mid-write.
language: rust
category: concurrency
rule_id: GRACEFUL-SHUTDOWN
priority: warn
tags:
- concurrency
- async
- shutdown
- cancellation
- rust-skills
---
Give long-running tasks an explicit shutdown signal, such as
tokio_util's CancellationToken or a watch channel. Select on it in their
loops, then wait for them to finish before main returns. Dropping the
runtime kills tasks mid-write.

## Good

- async fn run_worker(queue: Queue, shutdown: CancellationToken) {
    loop {
        tokio::select! {
            () = shutdown.cancelled() => break,
            Some(job) = queue.next() => process(job).await,
        }
    }
    queue.flush().await;
}

## Bad

- tokio::spawn(async move {
    loop {
        process(queue.next().await).await; // no way to stop it cleanly
    }
});
