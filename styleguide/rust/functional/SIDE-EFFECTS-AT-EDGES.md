---
type: Styleguide Rule
description: |-
  Keep I/O, mutations, and side effects at system edges. Core
  logic should be pure transformations.
language: rust
category: functional
rule_id: SIDE-EFFECTS-AT-EDGES
priority: warn
tags:
- functional
- side-effects
- architecture
- carmack
---
Keep I/O, mutations, and side effects at system edges. Core
logic should be pure transformations.

## Good

- // Pure core
fn process_data(data: &Data) -> Result { ... }

// Side effects at edge
fn main() {
    let data = read_file().unwrap();
    let result = process_data(&data);
    write_file(&result).unwrap();
}

## Bad

- fn process_data(data: &Data) -> Result {
    log_event("Processing"); // Side effect mixed with logic
    let result = transform(data);
    update_global_state(result); // Side effect
    result
}
