---
type: Styleguide Rule
description: |-
  When you've proven bounds are correct, use iterators or get_unchecked
  to eliminate redundant checks. Document safety.
language: rust
category: optimization
rule_id: BOUNDS-CHECK-ELIMINATION
priority: info
tags:
- optimization
- bounds-checks
- unsafe
---
When you've proven bounds are correct, use iterators or get_unchecked
to eliminate redundant checks. Document safety.

## Good

- // Bounds checked in outer loop
for chunk in data.chunks_exact(4) {
    unsafe {
        // SAFETY: chunks_exact guarantees len == 4
        process_four(chunk.get_unchecked(0..4));
    }
}

## Bad

- // Redundant checks in tight loop
for i in 0..len {
    data[i]; data[i+1]; data[i+2]; data[i+3];
}
