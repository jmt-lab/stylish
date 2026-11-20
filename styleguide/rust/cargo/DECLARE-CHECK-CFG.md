---
type: Styleguide Rule
description: |-
  Declare every custom cfg name your code tests in [lints.rust]
  unexpected_cfgs check-cfg, or with cargo::rustc-check-cfg in build.rs,
  so a typo such as cfg(feature = "seride") or cfg(tokio_unstabel) warns
  instead of silently disabling code.
language: rust
category: cargo
rule_id: DECLARE-CHECK-CFG
priority: warn
tags:
- cargo
- lints
- cfg
- features
- rust-skills
---
Declare every custom cfg name your code tests in [lints.rust]
unexpected_cfgs check-cfg, or with cargo::rustc-check-cfg in build.rs,
so a typo such as cfg(feature = "seride") or cfg(tokio_unstabel) warns
instead of silently disabling code.

## Good

- [lints.rust]
unexpected_cfgs = { level = "warn", check-cfg = ["cfg(loom)", "cfg(fuzzing)"] }

## Bad

- [lints.rust]
unexpected_cfgs = "allow" # every cfg typo now compiles silently
