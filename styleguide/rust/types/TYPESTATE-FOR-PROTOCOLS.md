---
type: Styleguide Rule
description: |-
  When an object must move through states in order (unconnected,
  connected, authenticated), encode each state as a type, using
  PhantomData markers or separate structs, so calling an operation in the
  wrong state is a compile error. Reserve this for protocols with real
  misuse risk; a runtime enum is simpler otherwise.
language: rust
category: types
rule_id: TYPESTATE-FOR-PROTOCOLS
priority: info
tags:
- types
- typestate
- api-design
- phantom-data
- rust-skills
---
When an object must move through states in order (unconnected,
connected, authenticated), encode each state as a type, using
PhantomData markers or separate structs, so calling an operation in the
wrong state is a compile error. Reserve this for protocols with real
misuse risk; a runtime enum is simpler otherwise.

## Good

- pub struct Connection<State> { socket: TcpStream, state: PhantomData<State> }
pub struct Connected;
pub struct Authenticated;

impl Connection<Connected> {
    pub fn login(self, credentials: &Credentials) -> Result<Connection<Authenticated>, LoginError> { /* ... */ }
}

impl Connection<Authenticated> {
    pub fn query(&mut self, sql: &str) -> Result<Rows, QueryError> { /* ... */ }
}

## Bad

- impl Connection {
    pub fn query(&mut self, sql: &str) -> Result<Rows, QueryError> {
        if !self.logged_in {
            return NotLoggedInSnafu.fail(); // misuse found only at runtime
        }
        // ...
    }
}
