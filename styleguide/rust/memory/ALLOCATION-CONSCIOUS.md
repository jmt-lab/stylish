---
type: Styleguide Rule
description: |-
  Understand where allocations happen. Minimize allocations in hot paths —
  allocation is expensive in performance-critical code. Reuse buffers,
  use stack allocation, or pre-allocate when possible.
language: rust
category: memory
rule_id: ALLOCATION-CONSCIOUS
priority: warn
tags:
- memory
- performance
- carmack
- optimization
- allocations
---
Understand where allocations happen. Minimize allocations in hot paths —
allocation is expensive in performance-critical code. Reuse buffers,
use stack allocation, or pre-allocate when possible.

## Good

- // Reuse buffer across frames
struct FrameData {
    temp_buffer: Vec<u8>,
}
impl FrameData {
    fn reset(&mut self) {
        self.temp_buffer.clear(); // Reuse capacity
    }
}
- // Pre-allocated, reused each frame
struct FrameState {
    buffer: Vec<u8>,
}
impl FrameState {
    fn reset(&mut self) { self.buffer.clear(); }
}

## Bad

- // Allocate every frame
fn process_frame() {
    let buffer = vec![0; 4096]; // New allocation
}
