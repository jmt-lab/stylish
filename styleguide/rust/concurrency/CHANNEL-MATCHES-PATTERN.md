---
type: Styleguide Rule
description: |-
  Pick the channel that matches the communication pattern: mpsc for a work
  queue with one consumer, oneshot for a single reply, broadcast when
  every subscriber must see every message, and watch when observers only
  need the latest value.
language: rust
category: concurrency
rule_id: CHANNEL-MATCHES-PATTERN
priority: info
tags:
- concurrency
- async
- channels
- rust-skills
---
Pick the channel that matches the communication pattern: mpsc for a work
queue with one consumer, oneshot for a single reply, broadcast when
every subscriber must see every message, and watch when observers only
need the latest value.

## Good

- struct Request {
    query: Query,
    reply: tokio::sync::oneshot::Sender<Answer>,
}

- // Readers only care about the current config, not every revision.
let (config_tx, config_rx) = tokio::sync::watch::channel(initial_config);

## Bad

- // An mpsc channel with capacity 1 used to return a single answer.
let (reply_tx, mut reply_rx) = tokio::sync::mpsc::channel::<Answer>(1);

- // broadcast for config updates: slow readers lag and miss the
// latest value they actually needed.
let (config_tx, _) = tokio::sync::broadcast::channel(16);
