---
type: Styleguide Rule
description: |-
  When drop order matters, use ManuallyDrop to control when resources
  are freed.
language: rust
category: memory
rule_id: MANUAL-DROP-ORDER
priority: info
tags:
- memory
- drop
- resources
---
When drop order matters, use ManuallyDrop to control when resources
are freed.

## Good

- use std::mem::ManuallyDrop;
struct System {
    resource: ManuallyDrop<Resource>,
}
impl Drop for System {
    fn drop(&mut self) {
        // Custom cleanup before resource drops
        unsafe { ManuallyDrop::drop(&mut self.resource); }
    }
}

## Bad

- // Unpredictable drop order in struct fields
