---
type: Styleguide Rule
description: |-
  When a package ships several executables, put each in src/bin/<name>.rs
  (or src/bin/<name>/main.rs) on top of the shared src/lib.rs, instead of
  [[bin]] entries pointing at ad-hoc paths or copy-pasted logic in each
  main.
language: rust
category: organization
rule_id: SRC-BIN-FOR-MULTIPLE-BINARIES
priority: info
tags:
- organization
- binaries
- cargo
- rust-skills
---
When a package ships several executables, put each in src/bin/<name>.rs
(or src/bin/<name>/main.rs) on top of the shared src/lib.rs, instead of
[[bin]] entries pointing at ad-hoc paths or copy-pasted logic in each
main.

## Good

- src/
├── lib.rs
└── bin/
    ├── server.rs
    └── migrate.rs

## Bad

- src/
├── main.rs
├── server_main.rs    # [[bin]] path = "src/server_main.rs"
└── migrate_main.rs   # duplicates half of main.rs
