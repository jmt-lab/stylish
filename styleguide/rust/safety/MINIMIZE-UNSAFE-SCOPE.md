---
type: Styleguide Rule
description: |-
  Keep each unsafe block as small as the one operation that needs it. Safe
  setup and follow-up code stay outside, so the SAFETY comment covers
  exactly one obligation and the compiler still checks everything else
  (Clippy: multiple_unsafe_ops_per_block).
language: rust
category: safety
rule_id: MINIMIZE-UNSAFE-SCOPE
priority: warn
tags:
- unsafe
- safety
- rust-skills
---
Keep each unsafe block as small as the one operation that needs it. Safe
setup and follow-up code stay outside, so the SAFETY comment covers
exactly one obligation and the compiler still checks everything else
(Clippy: multiple_unsafe_ops_per_block).

## Good

- let index = compute_index(key);
assert!(index < self.slots.len(), "index {index} out of bounds");
// SAFETY: the assert above guarantees `index` is in bounds.
let slot = unsafe { self.slots.get_unchecked(index) };
slot.validate()

## Bad

- unsafe {
    let index = compute_index(key);
    let slot = self.slots.get_unchecked(index);
    slot.validate()
}
