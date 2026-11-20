---
type: Styleguide Rule
description: |-
  Use std::thread::scope when threads only need to borrow data from the
  current stack frame. Scoped threads are joined before the scope returns,
  so they can borrow without Arc, clone, or 'static bounds.
language: rust
category: concurrency
rule_id: SCOPED-THREADS-FOR-BORROWS
priority: info
tags:
- concurrency
- threads
- ownership
- rust-skills
---
Use std::thread::scope when threads only need to borrow data from the
current stack frame. Scoped threads are joined before the scope returns,
so they can borrow without Arc, clone, or 'static bounds.

## Good

- let (left, right) = samples.split_at(samples.len() / 2);
let (left_sum, right_sum) = std::thread::scope(|scope| {
    let left = scope.spawn(|| left.iter().sum::<u64>());
    let right = scope.spawn(|| right.iter().sum::<u64>());
    (left.join().expect("left half panicked"), right.join().expect("right half panicked"))
});

## Bad

- let samples = Arc::new(samples.to_vec()); // clone only to satisfy 'static
let worker_samples = Arc::clone(&samples);
let handle = std::thread::spawn(move || worker_samples.iter().sum::<u64>());
