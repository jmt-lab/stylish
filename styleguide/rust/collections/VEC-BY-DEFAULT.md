---
type: Styleguide Rule
description: |-
  Default to Vec for sequences. Use VecDeque when you push or pop at both
  ends and BinaryHeap for a priority queue. Almost never use LinkedList:
  it is slower than Vec for nearly every workload because of poor cache
  locality.
language: rust
category: collections
rule_id: VEC-BY-DEFAULT
priority: info
tags:
- collections
- sequences
- performance
- rust-skills
---
Default to Vec for sequences. Use VecDeque when you push or pop at both
ends and BinaryHeap for a priority queue. Almost never use LinkedList:
it is slower than Vec for nearly every workload because of poor cache
locality.

## Good

- let mut pending: VecDeque<Job> = VecDeque::new();
pending.push_back(job);
let next = pending.pop_front();

- let mut timers: BinaryHeap<Reverse<Deadline>> = BinaryHeap::new();

## Bad

- let mut pending: Vec<Job> = Vec::new();
let next = pending.remove(0); // O(n) shift on every pop

- let mut items: LinkedList<Item> = LinkedList::new();
