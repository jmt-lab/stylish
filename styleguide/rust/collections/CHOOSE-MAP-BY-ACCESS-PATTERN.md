---
type: Styleguide Rule
description: |-
  Pick the map for how it is used: HashMap for fast unordered lookup,
  BTreeMap when you need sorted iteration, range queries, or deterministic
  output, and indexmap::IndexMap when insertion order must be preserved.
language: rust
category: collections
rule_id: CHOOSE-MAP-BY-ACCESS-PATTERN
priority: info
tags:
- collections
- maps
- performance
- rust-skills
---
Pick the map for how it is used: HashMap for fast unordered lookup,
BTreeMap when you need sorted iteration, range queries, or deterministic
output, and indexmap::IndexMap when insertion order must be preserved.

## Good

- let mut by_timestamp: BTreeMap<Timestamp, Event> = BTreeMap::new();
let recent = by_timestamp.range(cutoff..);

## Bad

- let mut by_timestamp: HashMap<Timestamp, Event> = HashMap::new();
let mut recent: Vec<_> = by_timestamp.iter().filter(|(time, _)| **time >= cutoff).collect();
recent.sort_by_key(|(time, _)| **time); // re-sorting what a BTreeMap gives for free
