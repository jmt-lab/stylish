---
type: Reference
description: The stylish clippy.toml to place next to Cargo.toml alongside the [lints] table.
---
# clippy.toml

```toml
# stylish clippy configuration. Copy next to Cargo.toml alongside the [lints] block
# from lints.toml. Adapted from BeautifulRust (MIT, Copyright (c) 2026 Morgan Linton).

# ENUM-OVER-BOOL-PARAMS: flag functions with more than one bool parameter. A single
# obvious bool (set_visible(true)) is allowed; use an enum when the meaning is unclear.
max-fn-params-bools = 1

# Tests may unwrap, expect, and print; a panic is the assertion.
allow-unwrap-in-tests = true
allow-expect-in-tests = true
allow-print-in-tests = true
```
