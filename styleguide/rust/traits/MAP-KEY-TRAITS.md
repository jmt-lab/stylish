---
type: Styleguide Rule
description: |-
  If a type is likely to be used as a map/set key or cached, implement Hash
  and Eq; if it also has a clear total ordering, implement Ord (and its
  prerequisites). For plain == or < support, prefer PartialEq / PartialOrd
  and only add Eq / Ord when reflexivity / total ordering truly hold.
language: rust
category: traits
rule_id: MAP-KEY-TRAITS
priority: info
tags:
- traits
- hash
- eq
- ord
- collections
- google-style
---
If a type is likely to be used as a map/set key or cached, implement Hash
and Eq; if it also has a clear total ordering, implement Ord (and its
prerequisites). For plain == or < support, prefer PartialEq / PartialOrd
and only add Eq / Ord when reflexivity / total ordering truly hold.

## Good

- #[derive(Clone, Debug, PartialEq, Eq, Hash, PartialOrd, Ord)]
pub struct ResourceId(String);
- #[derive(Debug, PartialEq, PartialOrd)]
pub struct Measurement { value: f64 } // f64 has no total order: no Eq/Ord

## Bad

- #[derive(Debug, PartialEq)]
pub struct ResourceId(String); // can't be a HashMap key
- #[derive(PartialEq, Eq)]
pub struct Measurement { value: f64 } // NaN != NaN violates Eq
