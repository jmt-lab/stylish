---
type: Styleguide Rule
description: |-
  Most types should implement Clone unless they represent an external
  resource (file handle, socket, lock guard). Implement Copy when it is
  reasonably clear the type will stay Copy in the future. Low-level library
  code should anticipate these needs; application code may add them as
  needed.
language: rust
category: traits
rule_id: IMPLEMENT-CLONE-BY-DEFAULT
priority: info
tags:
- traits
- clone
- copy
- google-style
---
Most types should implement Clone unless they represent an external
resource (file handle, socket, lock guard). Implement Copy when it is
reasonably clear the type will stay Copy in the future. Low-level library
code should anticipate these needs; application code may add them as
needed.

## Good

- #[derive(Clone, Debug)]
pub struct Settings { pub retries: u32, pub endpoint: String }
- #[derive(Clone, Copy, Debug, PartialEq, Eq)]
pub struct Rgb { r: u8, g: u8, b: u8 }

## Bad

- #[derive(Clone)]
pub struct Connection { socket: TcpStream } // duplicating a live connection is surprising
- #[derive(Clone, Copy)]
pub struct Request { id: u64 } // about to gain a String body; Copy will have to be removed
