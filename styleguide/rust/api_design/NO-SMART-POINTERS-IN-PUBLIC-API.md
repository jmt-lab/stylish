---
type: Styleguide Rule
description: |-
  Keep Rc, Arc, Box, RefCell, and Mutex out of public signatures. Take
  &T, &mut T, or T and let callers choose how to own things. Expose them only
  when shared ownership is fundamental to the API or benchmarks justify it.
language: rust
category: api_design
rule_id: NO-SMART-POINTERS-IN-PUBLIC-API
priority: warn
tags:
- api-design
- ownership
- smart-pointers
- beautiful-rust
---
Keep Rc, Arc, Box, RefCell, and Mutex out of public signatures. Take
&T, &mut T, or T and let callers choose how to own things. Expose them only
when shared ownership is fundamental to the API or benchmarks justify it.

## Good

- pub fn render(scene: &Scene) -> Image { ... }

## Bad

- pub fn render(scene: Rc<RefCell<Scene>>) -> Box<Image> { ... }
