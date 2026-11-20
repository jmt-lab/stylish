---
type: Styleguide Rule
description: |-
  Use bounded channels between producers and consumers so a slow consumer
  applies backpressure instead of letting the queue grow without limit.
  Reserve unbounded channels for cases where the producer count and
  message rate are provably small, and say why in a comment.
language: rust
category: concurrency
rule_id: BOUNDED-CHANNELS
priority: warn
tags:
- concurrency
- async
- channels
- backpressure
- rust-skills
---
Use bounded channels between producers and consumers so a slow consumer
applies backpressure instead of letting the queue grow without limit.
Reserve unbounded channels for cases where the producer count and
message rate are provably small, and say why in a comment.

## Good

- /// Holds at most one second of events at peak ingest rate.
const EVENT_QUEUE_CAPACITY: usize = 1_024;

let (sender, receiver) = tokio::sync::mpsc::channel(EVENT_QUEUE_CAPACITY);
sender.send(event).await?; // waits when the consumer falls behind

## Bad

- let (sender, receiver) = tokio::sync::mpsc::unbounded_channel();
sender.send(event)?; // memory grows until the process is killed
