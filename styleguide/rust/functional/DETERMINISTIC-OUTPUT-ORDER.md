---
type: Styleguide Rule
description: |-
  Never let HashMap / HashSet iteration order reach output, serialization,
  or test expectations. Use BTreeMap, an IndexMap, or sort before emitting
  when order is observable.
language: rust
category: functional
rule_id: DETERMINISTIC-OUTPUT-ORDER
priority: warn
tags:
- collections
- determinism
- testing
- beautiful-rust
---
Never let HashMap / HashSet iteration order reach output, serialization,
or test expectations. Use BTreeMap, an IndexMap, or sort before emitting
when order is observable.

## Good

- let mut counts: Vec<_> = word_counts.into_iter().collect();
counts.sort_by(|a, b| b.1.cmp(&a.1).then_with(|| a.0.cmp(&b.0)));
- let report: BTreeMap<String, u32> = ...;

## Bad

- for (word, count) in &word_counts { // HashMap: order changes between runs
    writeln!(out, "{word}: {count}")?;
}
