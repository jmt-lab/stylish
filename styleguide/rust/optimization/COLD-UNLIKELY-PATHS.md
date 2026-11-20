---
type: Styleguide Rule
description: |-
  Mark rarely executed functions, such as error construction, slow-path
  fallbacks, and panic helpers, with #[cold] (and #[inline(never)] when
  they are large). The compiler then keeps them out of the hot path's
  instruction cache and lays out the common branch first.
language: rust
category: optimization
rule_id: COLD-UNLIKELY-PATHS
priority: info
tags:
- optimization
- inlining
- branches
- rust-skills
---
Mark rarely executed functions, such as error construction, slow-path
fallbacks, and panic helpers, with #[cold] (and #[inline(never)] when
they are large). The compiler then keeps them out of the hot path's
instruction cache and lays out the common branch first.

## Good

- #[cold]
#[inline(never)]
fn capacity_exceeded(len: usize, capacity: usize) -> ! {
    panic!("buffer length {len} exceeds capacity {capacity}");
}

if self.len == self.capacity { capacity_exceeded(self.len, self.capacity); }

## Bad

- if self.len == self.capacity {
    // large formatting code inlined into every push
    panic!("buffer length {} exceeds capacity {}", self.len, self.capacity);
}
