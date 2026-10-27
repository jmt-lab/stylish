---
type: Styleguide Rule
description: |-
  If a From impl is one of the primary ways to construct a type, also
  provide an inherent constructor (::new(), ::new_from_foo(), or
  ::from_foo()) so the conversion is discoverable in the type's own docs.
language: rust
category: traits
rule_id: PAIR-FROM-WITH-CONSTRUCTOR
priority: info
tags:
- traits
- constructors
- discoverability
- google-style
---
If a From impl is one of the primary ways to construct a type, also
provide an inherent constructor (::new(), ::new_from_foo(), or
::from_foo()) so the conversion is discoverable in the type's own docs.

## Good

- impl Celsius {
    pub fn from_fahrenheit(f: Fahrenheit) -> Self { ... }
}

impl From<Fahrenheit> for Celsius {
    fn from(f: Fahrenheit) -> Self { Self::from_fahrenheit(f) }
}

## Bad

- impl From<Fahrenheit> for Celsius { ... }
// the only way to construct a Celsius from Fahrenheit is the blanket .into()
