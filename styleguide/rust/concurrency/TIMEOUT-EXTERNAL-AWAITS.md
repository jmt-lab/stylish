---
type: Styleguide Rule
description: |-
  Bound every await on something outside the process (network, IPC, a peer
  task) with a timeout, either through the client's own timeout setting or
  tokio::time::timeout. An await with no deadline can hang a task forever.
language: rust
category: concurrency
rule_id: TIMEOUT-EXTERNAL-AWAITS
priority: warn
tags:
- concurrency
- async
- timeouts
- resilience
- rust-skills
---
Bound every await on something outside the process (network, IPC, a peer
task) with a timeout, either through the client's own timeout setting or
tokio::time::timeout. An await with no deadline can hang a task forever.

## Good

- /// Upstream p99 is 300 ms; anything past 2 s is treated as down.
const UPSTREAM_TIMEOUT: Duration = Duration::from_secs(2);

let response = tokio::time::timeout(UPSTREAM_TIMEOUT, client.get(url).send())
    .await
    .context(UpstreamTimeoutSnafu { url })?
    .context(UpstreamRequestSnafu { url })?;

## Bad

- let response = client.get(url).send().await?; // may never return
