---
type: Styleguide Rule
description: Types, traits, and enums should use UpperCamelCase (PascalCase).
language: rust
category: naming
rule_id: UPPER-CAMEL-TYPES
priority: error
pattern: ^[A-Z][A-Za-z0-9]*$
tags:
- naming
- convention
- official
---
Types, traits, and enums should use UpperCamelCase (PascalCase).

## Good

- struct MyStruct {}
- enum ErrorType {}
- trait Renderable {}

## Bad

- struct my_struct {}
- enum error_type {}
