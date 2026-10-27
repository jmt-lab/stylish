---
type: Styleguide Rule
description: |-
  Don't write unsafe code unless the functionality cannot be implemented
  safely. When you must, wrap it in a small safe abstraction isolated from
  business logic (ideally its own module or crate), and justify why a safe
  equivalent isn't used; if the reason is performance, point to benchmarks.
language: rust
category: safety
rule_id: ENCAPSULATE-UNSAFE
priority: error
tags:
- safety
- unsafe
- encapsulation
- google-style
---
Don't write unsafe code unless the functionality cannot be implemented
safely. When you must, wrap it in a small safe abstraction isolated from
business logic (ideally its own module or crate), and justify why a safe
equivalent isn't used; if the reason is performance, point to benchmarks.

## Good

- /// Safe wrapper; see `ring_buffer::raw` for the justified unsafe core.
pub fn push(&mut self, value: T) {
    // SAFETY: `ensure_capacity` guarantees `self.len < self.cap`.
    unsafe { self.raw.write(self.len, value) };
    self.len += 1;
}
// Unsafe used because `benches/ring_buffer.rs` shows a 3x win over VecDeque.

## Bad

- fn handle_order(order: &Order) {
    let total = unsafe { *order.items.as_ptr().add(order.items.len() - 1) }; // in business logic
    ...
}
- let s = unsafe { String::from_utf8_unchecked(bytes) }; // str::from_utf8 would do
