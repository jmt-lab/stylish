---
type: Styleguide Rule
description: |-
  In library function parameters, prefer generics (T: Trait or impl Trait)
  over dyn Trait. Generics avoid vtable indirection, allow inlining, and work
  with traits that aren't dyn compatible. Use dyn Trait where code size
  matters or for heterogeneous collections.
language: rust
category: traits
rule_id: GENERICS-OVER-DYN-IN-LIBRARIES
priority: info
tags:
- traits
- generics
- dyn
- performance
- libraries
- google-style
---
In library function parameters, prefer generics (T: Trait or impl Trait)
over dyn Trait. Generics avoid vtable indirection, allow inlining, and work
with traits that aren't dyn compatible. Use dyn Trait where code size
matters or for heterogeneous collections.

## Good

- pub fn write_report(out: &mut impl Write, report: &Report) -> io::Result<()> { ... }
- let handlers: Vec<Box<dyn Handler>> = ...; // heterogeneous collection

## Bad

- pub fn write_report(out: &mut dyn Write, report: &Report) -> io::Result<()> { ... }
