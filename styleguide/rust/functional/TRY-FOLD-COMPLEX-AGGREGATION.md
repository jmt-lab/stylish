---
type: Styleguide Rule
description: |-
  When aggregating with possible failure, try_fold combines
  folding with error handling cleanly.
language: rust
category: functional
rule_id: TRY-FOLD-COMPLEX-AGGREGATION
priority: info
tags:
- functional
- fold
- error-handling
---
When aggregating with possible failure, try_fold combines
folding with error handling cleanly.

## Good

- items.iter().try_fold(initial, |acc, item| {
    let value = item.validate()?;
    Ok(acc + value)
})?

## Bad

- let mut acc = initial;
for item in items {
    let value = item.validate()?;
    acc += value;
}
