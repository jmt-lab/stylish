---
type: Styleguide Rule
description: |-
  Give assert! (and debug_assert!) a context message explaining why the
  condition should hold, logging relevant values, or saying whether a failure
  is API misuse or an internal bug. Use the message instead of a comment so it
  appears in logs. Don't merely restate the condition.
language: rust
category: error_handling
rule_id: ASSERT-CONTEXT-MESSAGES
priority: warn
tags:
- error-handling
- assertions
- debugging
- google-style
---
Give assert! (and debug_assert!) a context message explaining why the
condition should hold, logging relevant values, or saying whether a failure
is API misuse or an internal bug. Use the message instead of a comment so it
appears in logs. Don't merely restate the condition.

## Good

- assert!(
    values.is_sorted(),
    "`values` comes from a PriorityQueue, so it should already be sorted"
);
- assert!(refund > 0, "refund must be positive, got {refund:?}");
- assert!(self.stream.is_some(), "call connect() before executing queries");

## Bad

- assert!(values.is_sorted(), "values should be sorted");
- // The queue guarantees ordering.
assert!(values.is_sorted());
