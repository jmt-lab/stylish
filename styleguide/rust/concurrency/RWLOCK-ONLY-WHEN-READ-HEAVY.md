---
type: Styleguide Rule
description: |-
  Default to Mutex. Reach for RwLock only when reads greatly outnumber
  writes, critical sections are long enough to matter, and a profile shows
  contention. RwLock costs more per operation, and some implementations
  let writers starve.
language: rust
category: concurrency
rule_id: RWLOCK-ONLY-WHEN-READ-HEAVY
priority: info
tags:
- concurrency
- locks
- performance
- rust-skills
---
Default to Mutex. Reach for RwLock only when reads greatly outnumber
writes, critical sections are long enough to matter, and a profile shows
contention. RwLock costs more per operation, and some implementations
let writers starve.

## Good

- // Read on every request, rewritten once a minute; profiled as contended.
routes: RwLock<RouteTable>,

- counters: Mutex<HashMap<Endpoint, u64>>, // every access writes

## Bad

- counters: RwLock<HashMap<Endpoint, u64>>, // every access takes the write lock anyway
