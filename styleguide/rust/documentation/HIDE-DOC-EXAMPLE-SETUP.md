---
type: Styleguide Rule
description: |-
  Prefix setup lines in doc examples (imports, fn main wrappers, fixtures)
  with # so they compile and run but don't clutter the rendered docs. Keep
  visible only the lines that show the API.
language: rust
category: documentation
rule_id: HIDE-DOC-EXAMPLE-SETUP
priority: info
tags:
- documentation
- examples
- doctests
- rust-skills
---
Prefix setup lines in doc examples (imports, fn main wrappers, fixtures)
with # so they compile and run but don't clutter the rendered docs. Keep
visible only the lines that show the API.

## Good

- /// ```
/// # use inventory::{Inventory, Sku};
/// # fn main() -> Result<(), Box<dyn std::error::Error>> {
/// let mut inventory = Inventory::new();
/// inventory.add(Sku::new("A-100")?, 3);
/// assert_eq!(inventory.count(&Sku::new("A-100")?), 3);
/// # Ok(())
/// # }
/// ```

## Bad

- /// ```ignore
/// inventory.add(sku, 3); // doesn't compile on its own, so it is never tested
/// ```
