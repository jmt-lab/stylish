---
type: Styleguide Rule
description: |-
  Name accessors consistently: foo() returns &T (or T if Copy), foo_mut()
  returns &mut T, set_foo() sets by value, take_foo() clears the field and
  returns the old value, replace_foo() sets and returns the old value, and
  with_foo() / with_mut_foo() passes the value to a closure (useful when it
  lives behind a Mutex or RefCell, so guards don't leak).
language: rust
category: naming
rule_id: ACCESSOR-NAMING
priority: warn
tags:
- naming
- getters
- setters
- accessors
- google-style
---
Name accessors consistently: foo() returns &T (or T if Copy), foo_mut()
returns &mut T, set_foo() sets by value, take_foo() clears the field and
returns the old value, replace_foo() sets and returns the old value, and
with_foo() / with_mut_foo() passes the value to a closure (useful when it
lives behind a Mutex or RefCell, so guards don't leak).

## Good

- impl Session {
    pub fn token(&self) -> &Token { ... }
    pub fn token_mut(&mut self) -> &mut Token { ... }
    pub fn take_token(&mut self) -> Option<Token> { ... }
    pub fn replace_token(&mut self, token: Token) -> Token { ... }
    pub fn with_cache<R>(&self, f: impl FnOnce(&Cache) -> R) -> R { ... }
}

## Bad

- impl Session {
    pub fn get_token_mutable(&mut self) -> &mut Token { ... }
    pub fn clear_and_get_token(&mut self) -> Option<Token> { ... }
    pub fn cache(&self) -> MutexGuard<'_, Cache> { ... } // leaks locking detail
}
