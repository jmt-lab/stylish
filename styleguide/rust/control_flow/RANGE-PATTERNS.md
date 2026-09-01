---
type: Styleguide Rule
description: |-
  Range patterns make numeric matching clearer and more
  maintainable than multiple conditions.
language: rust
category: control_flow
rule_id: RANGE-PATTERNS
priority: info
tags:
- control-flow
- pattern-matching
- clarity
---
Range patterns make numeric matching clearer and more
maintainable than multiple conditions.

## Good

- match score {
    0..=59 => Grade::F,
    60..=69 => Grade::D,
    70..=79 => Grade::C,
    80..=89 => Grade::B,
    90..=100 => Grade::A,
    _ => panic!("Invalid score"),
}

## Bad

- if score < 60 { Grade::F }
else if score < 70 { Grade::D }
...
