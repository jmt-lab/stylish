---
type: Styleguide Rule
description: |-
  Accept impl Into<T> only in library APIs where call-site ergonomics are
  paramount and callers are likely to hold various convertible types. Weigh
  it against code bloat, more complex signatures, and inference problems.
  Application code should almost never take impl Into<T> parameters.
language: rust
category: api_design
rule_id: IMPL-INTO-SPARINGLY
priority: info
tags:
- api-design
- generics
- parameters
- google-style
---
Accept impl Into<T> only in library APIs where call-site ergonomics are
paramount and callers are likely to hold various convertible types. Weigh
it against code bloat, more complex signatures, and inference problems.
Application code should almost never take impl Into<T> parameters.

## Good

- pub fn new(name: impl Into<String>) -> Self { Self { name: name.into() } } // widely used library type
- fn record_event(name: String) { ... } // application code

## Bad

- fn record_event(name: impl Into<String>, source: impl Into<PathBuf>, tag: impl Into<Tag>) { ... } // internal helper
