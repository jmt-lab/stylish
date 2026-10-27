---
type: Styleguide Rule
description: |-
  If a function needs to own its argument (to store or consume it), take
  it by value and let the caller decide whether to clone. Never take &T and
  clone it internally. Take &T to read and &mut T to mutate in place.
language: rust
category: api_design
rule_id: TAKE-OWNERSHIP-BY-VALUE
priority: warn
tags:
- api-design
- ownership
- clone
- beautiful-rust
---
If a function needs to own its argument (to store or consume it), take
it by value and let the caller decide whether to clone. Never take &T and
clone it internally. Take &T to read and &mut T to mutate in place.

## Good

- pub fn set_name(&mut self, name: String) {
    self.name = name;
}

## Bad

- pub fn set_name(&mut self, name: &String) {
    self.name = name.clone(); // hidden allocation the caller can't avoid
}
