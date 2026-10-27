---
type: Styleguide Rule
description: |-
  Prefer message passing (channels, actors) to shared mutable state when
  coordinating concurrent work. Use shared state only when it is simpler or
  measurably faster.
language: rust
category: concurrency
rule_id: PREFER-MESSAGE-PASSING
priority: info
tags:
- concurrency
- channels
- design
- beautiful-rust
---
Prefer message passing (channels, actors) to shared mutable state when
coordinating concurrent work. Use shared state only when it is simpler or
measurably faster.

## Good

- let (tx, rx) = mpsc::channel();
for path in paths { let tx = tx.clone(); thread::spawn(move || tx.send(hash(&path))); }
let hashes: Vec<_> = rx.iter().take(count).collect();

## Bad

- let results = Arc::new(Mutex::new(Vec::new()));
// every worker locks the same Vec to push one item
