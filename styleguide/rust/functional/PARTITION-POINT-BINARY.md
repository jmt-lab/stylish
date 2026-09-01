---
type: Styleguide Rule
description: |-
  For sorted data, partition_point provides clean binary search
  without manual index management.
language: rust
category: functional
rule_id: PARTITION-POINT-BINARY
priority: info
tags:
- functional
- search
- algorithms
---
For sorted data, partition_point provides clean binary search
without manual index management.

## Good

- let index = sorted.partition_point(|x| x < &target);

## Bad

- let mut low = 0;
let mut high = sorted.len();
while low < high {
    let mid = (low + high) / 2;
    // Manual binary search
}
