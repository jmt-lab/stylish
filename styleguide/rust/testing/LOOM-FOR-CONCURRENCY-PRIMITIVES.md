---
type: Styleguide Rule
description: |-
  Test hand-written lock-free structures, custom synchronization
  primitives, and atomics-based protocols with loom, which explores the
  possible thread interleavings. An ordinary test exercises only the one
  interleaving that happens to occur.
language: rust
category: testing
rule_id: LOOM-FOR-CONCURRENCY-PRIMITIVES
priority: info
tags:
- testing
- concurrency
- atomics
- loom
- rust-skills
---
Test hand-written lock-free structures, custom synchronization
primitives, and atomics-based protocols with loom, which explores the
possible thread interleavings. An ordinary test exercises only the one
interleaving that happens to occur.

## Good

- #[cfg(loom)]
#[test]
fn test_spsc_queue_never_loses_items() {
    loom::model(|| {
        let queue = Arc::new(SpscQueue::new(1));
        let producer = {
            let queue = Arc::clone(&queue);
            loom::thread::spawn(move || queue.push(7))
        };
        let popped = queue.pop();
        producer.join().expect("producer panicked");
        assert!(popped == Some(7) || queue.pop() == Some(7));
    });
}

## Bad

- #[test]
fn test_spsc_queue_never_loses_items() {
    for _ in 0..10_000 { /* hope the race shows up */ }
}
