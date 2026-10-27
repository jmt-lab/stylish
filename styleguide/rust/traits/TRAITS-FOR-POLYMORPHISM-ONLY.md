---
type: Styleguide Rule
description: |-
  Define a trait only to enable generic programming (T: Trait bounds), to
  accept or return impl Trait / dyn Trait, or as an extension trait. In all
  other cases use an inherent impl. Don't use traits merely to organize
  code.
language: rust
category: traits
rule_id: TRAITS-FOR-POLYMORPHISM-ONLY
priority: warn
tags:
- traits
- api-design
- simplicity
- google-style
---
Define a trait only to enable generic programming (T: Trait bounds), to
accept or return impl Trait / dyn Trait, or as an extension trait. In all
other cases use an inherent impl. Don't use traits merely to organize
code.

## Good

- impl Parser {
    pub fn parse(&self, input: &str) -> Result<Ast, ParseError> { ... }
}
- pub trait Storage { fn get(&self, key: &str) -> Option<Bytes>; }
fn serve(store: &impl Storage) { ... } // multiple implementations

## Bad

- trait ParserOps {
    fn parse(&self, input: &str) -> Result<Ast, ParseError>;
}
impl ParserOps for Parser { ... } // single implementor, never used generically
