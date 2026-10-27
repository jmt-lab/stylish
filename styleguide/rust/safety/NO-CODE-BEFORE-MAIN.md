---
type: Styleguide Rule
description: |-
  Don't run code before main(), e.g. via the ctor crate or link-section
  tricks. Pre-main code has unclear ordering and environment guarantees. Use
  explicit initialization or LazyLock instead.
language: rust
category: safety
rule_id: NO-CODE-BEFORE-MAIN
priority: error
tags:
- safety
- initialization
- globals
- google-style
---
Don't run code before main(), e.g. via the ctor crate or link-section
tricks. Pre-main code has unclear ordering and environment guarantees. Use
explicit initialization or LazyLock instead.

## Good

- static REGISTRY: LazyLock<Registry> = LazyLock::new(Registry::load);
- fn main() {
    logging::init();
    ...
}

## Bad

- #[ctor::ctor]
fn init_logging() {
    logging::init();
}
