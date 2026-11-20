---
type: Styleguide Rule
description: |-
  Report invalid proc-macro input as a spanned compile error, using
  syn::Error::new_spanned(...).to_compile_error() or darling. Don't panic:
  a panic produces an opaque "proc macro panicked" message that points at
  no source location.
language: rust
category: macros
rule_id: PROC-MACRO-SPANNED-ERRORS
priority: warn
tags:
- macros
- proc-macro
- diagnostics
- rust-skills
---
Report invalid proc-macro input as a spanned compile error, using
syn::Error::new_spanned(...).to_compile_error() or darling. Don't panic:
a panic produces an opaque "proc macro panicked" message that points at
no source location.

## Good

- let Data::Struct(data) = &input.data else {
    return syn::Error::new_spanned(&input.ident, "Builder can only be derived for structs")
        .to_compile_error()
        .into();
};

## Bad

- let Data::Struct(data) = &input.data else {
    panic!("not a struct");
};
