---
type: Styleguide Rule
description: |-
  Use an associated type when each implementing type has exactly one
  natural choice, as with Iterator::Item. Use a generic parameter when one
  type can sensibly implement the trait for many types, as with From<T>.
  Associated types keep call sites free of turbofish and inference
  failures.
language: rust
category: traits
rule_id: ASSOCIATED-TYPE-VS-GENERIC-PARAMETER
priority: info
tags:
- traits
- generics
- api-design
- rust-skills
---
Use an associated type when each implementing type has exactly one
natural choice, as with Iterator::Item. Use a generic parameter when one
type can sensibly implement the trait for many types, as with From<T>.
Associated types keep call sites free of turbofish and inference
failures.

## Good

- trait Decoder {
    type Output;
    fn decode(&mut self, bytes: &[u8]) -> Result<Self::Output, DecodeError>;
}

- trait Render<Target> {
    fn render(&self, target: &mut Target);
}

impl Render<Terminal> for Chart { /* ... */ }
impl Render<Svg> for Chart { /* ... */ }

## Bad

- trait Decoder<Output> {
    // each decoder only ever produces one Output, yet every caller must name it
    fn decode(&mut self, bytes: &[u8]) -> Result<Output, DecodeError>;
}
