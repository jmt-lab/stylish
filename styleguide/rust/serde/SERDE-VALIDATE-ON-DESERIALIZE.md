---
type: Styleguide Rule
description: |-
  Validate during deserialization by deserializing into a raw type and
  converting with #[serde(try_from = "Raw")], or by deserializing straight
  into validated newtypes. A struct whose invariants hold after new() must
  not be constructible from JSON without them.
language: rust
category: serde
rule_id: SERDE-VALIDATE-ON-DESERIALIZE
priority: warn
tags:
- serde
- validation
- newtypes
- parse-dont-validate
- rust-skills
---
Validate during deserialization by deserializing into a raw type and
converting with #[serde(try_from = "Raw")], or by deserializing straight
into validated newtypes. A struct whose invariants hold after new() must
not be constructible from JSON without them.

## Good

- #[derive(Deserialize)]
#[serde(try_from = "RawPort")]
struct Port(NonZeroU16);

impl TryFrom<RawPort> for Port {
    type Error = InvalidPortError;

    fn try_from(raw: RawPort) -> Result<Self, Self::Error> {
        NonZeroU16::new(raw.0).map(Port).context(ZeroPortSnafu)
    }
}

## Bad

- #[derive(Deserialize)]
struct Port(u16); // Port::new rejects 0, but `"port": 0` deserializes fine
