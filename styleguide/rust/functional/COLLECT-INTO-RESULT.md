---
type: Styleguide Rule
description: |-
  To stop at the first error in an iterator pipeline, collect into
  Result<Vec<_>, E> (or Option<Vec<_>>) and apply ?, rather than looping with
  manual early returns or silently filtering errors out.
language: rust
category: functional
rule_id: COLLECT-INTO-RESULT
priority: info
tags:
- iterators
- error-handling
- collect
- beautiful-rust
---
To stop at the first error in an iterator pipeline, collect into
Result<Vec<_>, E> (or Option<Vec<_>>) and apply ?, rather than looping with
manual early returns or silently filtering errors out.

## Good

- let ports = inputs.iter().map(|s| s.parse::<u16>()).collect::<Result<Vec<_>, _>>()?;

## Bad

- let ports: Vec<u16> = inputs.iter().filter_map(|s| s.parse().ok()).collect(); // drops bad input silently
