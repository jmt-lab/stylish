---
type: Styleguide Rule
description: |-
  Lay out multi-crate projects as one workspace with crates as siblings
  under crates/, every crate a workspace member, never nested inside another
  crate or its src/. Prefer splitting into small single-purpose crates when
  a crate grows a second purpose.
language: rust
category: cargo
rule_id: FLAT-CRATES-WORKSPACE
priority: info
tags:
- cargo
- workspace
- organization
- beautiful-rust
---
Lay out multi-crate projects as one workspace with crates as siblings
under crates/, every crate a workspace member, never nested inside another
crate or its src/. Prefer splitting into small single-purpose crates when
a crate grows a second purpose.

## Good

- Cargo.toml          # [workspace] members = ["crates/*"]
crates/
  web-server/
  web-client/
  web-protocol/

## Bad

- Cargo.toml
src/
  client/
    Cargo.toml        # crate nested inside another crate's src/
