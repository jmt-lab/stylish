---
type: Styleguide Rule
description: |-
  A safe function must not be able to cause undefined behavior through any
  sequence of safe calls. The module containing the unsafe code is the
  soundness boundary: keep the invariant's fields private to it. If you can't
  encapsulate the invariant, expose an unsafe fn with a documented contract.
language: rust
category: safety
rule_id: NO-UNSOUND-ABSTRACTIONS
priority: error
tags:
- safety
- unsafe
- soundness
- beautiful-rust
---
A safe function must not be able to cause undefined behavior through any
sequence of safe calls. The module containing the unsafe code is the
soundness boundary: keep the invariant's fields private to it. If you can't
encapsulate the invariant, expose an unsafe fn with a documented contract.

## Good

- mod buffer {
    pub struct Buffer { data: Vec<u8>, len: usize } // private: only this module upholds len <= data.len()
    impl Buffer {
        pub fn as_slice(&self) -> &[u8] {
            // SAFETY: every constructor and mutator keeps len <= data.len().
            unsafe { self.data.get_unchecked(..self.len) }
        }
    }
}

## Bad

- pub struct Buffer { pub data: Vec<u8>, pub len: usize } // anyone can break len <= data.len()
impl Buffer {
    pub fn as_slice(&self) -> &[u8] { unsafe { self.data.get_unchecked(..self.len) } }
}
