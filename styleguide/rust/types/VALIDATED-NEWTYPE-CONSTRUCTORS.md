---
type: Styleguide Rule
description: |-
  A newtype that encodes an invariant (Month in 1..=12, NonEmptyName)
  validates in a fallible constructor (TryFrom, FromStr, or try_new) and never
  offers an infallible From from the raw type.
language: rust
category: types
rule_id: VALIDATED-NEWTYPE-CONSTRUCTORS
priority: warn
tags:
- types
- newtype
- validation
- invariants
- beautiful-rust
---
A newtype that encodes an invariant (Month in 1..=12, NonEmptyName)
validates in a fallible constructor (TryFrom, FromStr, or try_new) and never
offers an infallible From from the raw type.

## Good

- pub struct Month(u8);

impl TryFrom<u8> for Month {
    type Error = InvalidMonthError;
    fn try_from(value: u8) -> Result<Self, Self::Error> {
        ensure!((1..=12).contains(&value), InvalidMonthSnafu { value });
        Ok(Self(value))
    }
}

## Bad

- impl From<u8> for Month {
    fn from(value: u8) -> Self { Self(value) } // Month::from(42) compiles
}
