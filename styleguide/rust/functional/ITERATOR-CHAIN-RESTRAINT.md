---
type: Styleguide Rule
description: |-
  Use combinators where they say something concise (any, sum, a short
  map/filter), but switch to a for loop when a chain grows long, branches, or
  mutates outside state. Don't build chains in a for loop header; bind them
  to a well-named variable first. Avoid Iterator::for_each unless you have a
  good reason. This balances ITERATOR-CHAINS.
language: rust
category: functional
rule_id: ITERATOR-CHAIN-RESTRAINT
priority: warn
tags:
- iterators
- readability
- loops
- google-style
---
Use combinators where they say something concise (any, sum, a short
map/filter), but switch to a for loop when a chain grows long, branches, or
mutates outside state. Don't build chains in a for loop header; bind them
to a well-named variable first. Avoid Iterator::for_each unless you have a
good reason. This balances ITERATOR-CHAINS.

## Good

- let over_limit = values.iter().any(|&v| v > limit);
- let urgent_bugs = reports
    .iter()
    .filter_map(|report| parse_bug(report).ok())
    .filter(|bug| bug.priority <= Priority::P1);

for bug in urgent_bugs {
    assign(bug);
}
- for item in items {
    match transform(item) {
        Ok(value) => processed.push(value),
        Err(_) => error_count += 1,
    }
}

## Bad

- for bug in reports
    .iter()
    .filter_map(|report| parse_bug(report).ok())
    .filter(|bug| bug.priority <= Priority::P1)
{
    assign(bug);
}
- let processed: Vec<_> = items
    .into_iter()
    .map(transform)
    .map(|result| {
        if result.is_err() {
            error_count += 1;
        }
        result
    })
    .filter_map(Result::ok)
    .collect();
- users.iter().for_each(|user| notify(user));
