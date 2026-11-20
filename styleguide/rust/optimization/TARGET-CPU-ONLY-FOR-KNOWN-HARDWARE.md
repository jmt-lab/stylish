---
type: Styleguide Rule
description: |-
  Use -C target-cpu=native or profile-guided optimization only when you
  control the deployment hardware and have measured a benefit. A binary
  built for native can crash with an illegal instruction on older CPUs, so
  never ship one in published artifacts.
language: rust
category: optimization
rule_id: TARGET-CPU-ONLY-FOR-KNOWN-HARDWARE
priority: info
tags:
- optimization
- build
- pgo
- rust-skills
---
Use -C target-cpu=native or profile-guided optimization only when you
control the deployment hardware and have measured a benefit. A binary
built for native can crash with an illegal instruction on older CPUs, so
never ship one in published artifacts.

## Good

- # .cargo/config.toml for an internal service pinned to one instance family
[target.x86_64-unknown-linux-gnu]
rustflags = ["-C", "target-cpu=x86-64-v3"]

## Bad

- # .cargo/config.toml in a published CLI
[build]
rustflags = ["-C", "target-cpu=native"] # SIGILL on users' older machines
