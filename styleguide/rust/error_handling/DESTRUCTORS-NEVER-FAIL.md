---
type: Styleguide Rule
description: |-
  Drop implementations must not panic, block, or have failure modes. Offer
  an explicit close(self) -> Result<..> for fallible or blocking teardown and
  make Drop a best-effort fallback.
language: rust
category: error_handling
rule_id: DESTRUCTORS-NEVER-FAIL
priority: error
tags:
- error-handling
- drop
- raii
- beautiful-rust
---
Drop implementations must not panic, block, or have failure modes. Offer
an explicit close(self) -> Result<..> for fallible or blocking teardown and
make Drop a best-effort fallback.

## Good

- impl Writer {
    pub fn close(mut self) -> Result<(), FlushError> { self.flush_inner() }
}

impl Drop for Writer {
    fn drop(&mut self) {
        let _ = self.flush_inner(); // best effort; close() reports errors
    }
}

## Bad

- impl Drop for Writer {
    fn drop(&mut self) {
        self.flush_inner().expect("flush failed"); // panic during unwind aborts
    }
}
