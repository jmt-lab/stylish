---
type: Styleguide Rule
description: |-
  Use #[rustfmt::skip] only for deliberate manual alignment (e.g. a matrix
  or a table of similar lines) or for generated code. Never skip formatting
  for personal style preferences.
language: rust
category: formatting
rule_id: RUSTFMT-SKIP-SPARINGLY
priority: warn
tags:
- formatting
- rustfmt
- tooling
- google-style
---
Use #[rustfmt::skip] only for deliberate manual alignment (e.g. a matrix
or a table of similar lines) or for generated code. Never skip formatting
for personal style preferences.

## Good

- #[rustfmt::skip]
const IDENTITY: [[f32; 3]; 3] = [
    [1.0, 0.0, 0.0],
    [0.0, 1.0, 0.0],
    [0.0, 0.0, 1.0],
];

## Bad

- #[rustfmt::skip]
fn connect(host: &str, port: u16) -> Result<Conn> { let addr = (host, port); Conn::open(addr) }
// skipped only because the author prefers one-liners
