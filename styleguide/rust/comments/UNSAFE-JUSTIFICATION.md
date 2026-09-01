---
type: Styleguide Rule
description: |-
  Every unsafe block must have a SAFETY comment explaining why the
  invariants are upheld and the operation is actually safe.
language: rust
category: comments
rule_id: UNSAFE-JUSTIFICATION
priority: error
tags:
- unsafe
- safety
- documentation
---
Every unsafe block must have a SAFETY comment explaining why the
invariants are upheld and the operation is actually safe.

## Good

- unsafe {
    // SAFETY: ptr is valid for cap bytes (ensured in new()),
    // len < cap (checked above), and u8 has no alignment requirements
    std::ptr::write(ptr.add(len), byte);
}

## Bad

- unsafe {
    std::ptr::write(ptr.add(len), byte); // No safety comment
}
