---
type: Styleguide Rule
description: |-
  Don't fire and forget tokio::spawn. Keep the JoinHandle, or put dynamic
  groups of tasks in a JoinSet, so panics and errors are observed and
  tasks are aborted when their owner goes away.
language: rust
category: concurrency
rule_id: TRACK-SPAWNED-TASKS
priority: warn
tags:
- concurrency
- async
- tokio
- structured-concurrency
- rust-skills
---
Don't fire and forget tokio::spawn. Keep the JoinHandle, or put dynamic
groups of tasks in a JoinSet, so panics and errors are observed and
tasks are aborted when their owner goes away.

## Good

- let mut downloads = tokio::task::JoinSet::new();
for url in urls {
    downloads.spawn(download(client.clone(), url));
}
while let Some(result) = downloads.join_next().await {
    result.expect("download task panicked")?;
}

## Bad

- for url in urls {
    tokio::spawn(download(client.clone(), url)); // errors and panics vanish
}
