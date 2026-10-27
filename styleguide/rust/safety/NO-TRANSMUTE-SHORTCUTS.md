---
type: Styleguide Rule
description: |-
  Don't transmute to cast enums or integers, extend lifetimes, or bypass
  the type system, and don't write unsafe impl Send / Sync to silence the
  compiler. Use TryFrom, as for plain numeric casts, or restructure ownership.
language: rust
category: safety
rule_id: NO-TRANSMUTE-SHORTCUTS
priority: error
tags:
- safety
- unsafe
- transmute
- beautiful-rust
---
Don't transmute to cast enums or integers, extend lifetimes, or bypass
the type system, and don't write unsafe impl Send / Sync to silence the
compiler. Use TryFrom, as for plain numeric casts, or restructure ownership.

## Good

- let level = Level::try_from(raw).context(InvalidLevelSnafu { raw })?;

## Bad

- let level: Level = unsafe { mem::transmute(raw) }; // UB for out-of-range values
- unsafe impl Send for Handle {} // "it compiles now"
