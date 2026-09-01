---
type: Styleguide Rule
description: |-
  Carmack principle: Check error conditions early and return.
  Keeps happy path at main indentation level. Apply to both
  guard conditions and error handling — return Err early for
  invalid state so the main logic stays unindented.
language: rust
category: control_flow
rule_id: EARLY-RETURN-GUARDS
priority: warn
tags:
- control-flow
- readability
- carmack
- errors
---
Carmack principle: Check error conditions early and return.
Keeps happy path at main indentation level. Apply to both
guard conditions and error handling — return Err early for
invalid state so the main logic stays unindented.

## Good

- fn process(entity: &Entity) -> Result<()> {
    if !entity.is_valid() {
        return Err(Error::Invalid);
    }
    // Happy path at base level
}
- fn process(entity: &Entity) -> Result<(), Error> {
    if !entity.is_valid() {
        return Err(Error::InvalidEntity);
    }
    // Happy path
}

## Bad

- fn process(entity: &Entity) -> Result<()> {
    if entity.is_valid() {
        // Happy path nested
    } else {
        Err(Error::Invalid)
    }
}
